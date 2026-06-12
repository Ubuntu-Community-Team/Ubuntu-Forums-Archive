---
title: "how does gmail.pl work?"
date: 2011-03-01
forum: Desktop Environments
---

### Post by Arminius on 2011-03-01
I'm trying to get gmail onto my conky
and I've googled around and havent' found any instructions, I assume that this gmail.pl contains my email and the password? but I have no idea what other code must go with it?
this is the code that I lifted from someone else's conky

```
#################
##    GMAIL    ##
##################
${voffset 10}${font Radis sans:bold:size=10}${color2}GMAIL ${color8} ${hr 2}
You have ${color yellow}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new email messages.
${execi 60 perl ~/scripts/gmail.pl s}
```

---

### Post by themtx on 2011-03-01
Once you configure gmail.pl with your account settings (and I'd def chmod it to 700 once your login info is in there), you'll paste the above into your .conkyrc, which is usually in your home dir.

Here's the relevant section of my .conkyrc FYI, though I use a diff python script called gmail_parser.py

```
${execpi 300 python ~/.conky/gmail_parser.py username password 1}${color #b8b8b8}
```

Concept is the same.  Script can be googled.

---

### Post by Arminius on 2011-03-01
I'm afraid I don't understand what u mean by "configure gmail.pl with your account settings" and I have even less understanding of the "chmod it to 700 once your login info is in there"
so yeah if u could just point me in the right direction I'll try to figure out the rest.

---

### Post by lisati on 2011-03-01
> **Arminius said:**
> I'm afraid I don't understand what u mean by "configure gmail.pl with your account settings" and I have even less understanding of the "chmod it to 700 once your login info is in there"
so yeah if u could just point me in the right direction I'll try to figure out the rest.

Rough translation: Edit ~/scripts/gmail.pl so that it contains the proper settings to access *your* email account, and then set the Linux file permissions to limit who can access the file.

---

### Post by Arminius on 2011-03-01
yes but what are the correct settings for gmail.pl?
I've googled around and I'm not finding any templates
I assume it can't just be
```
username:myusername
password:mypassword
```

---

### Post by themtx on 2011-03-01
You'll edit the actual gmail.pl file you've saved somewhere on your machine with your account information, which is required to connect to gmail when the script executes from within conky.  The script will try to execute from within conky when you paste the text you quoted into your .conkyrc, assuming you have the gmail.pl file saved in ~/scripts/gmail.pl

chmod changes permissions on files from the command line.  Since you're saving critical account information in the file, I'd make sure no one but your user account has the ability to read the file, which is accomplished by typing chmod 700 gmail.pl from within the dir where the gmail.pl file is locate.

Hth.

---

### Post by Arminius on 2011-03-01
I haven't saved gmail.pl anywhere, I don't know what it's ment to contain, I figured maybe some other process of gmail might have already done it for me, if so I ran a serach of the hardrive and it's come up with nothing.???

---

### Post by Arminius on 2011-03-02
bump

---

### Post by stinkeye on 2011-03-02
Sounds to me like you don't have the gmail.pl script that conky is calling.
This is the one I use and appears to be the same one used in your conky.
To work with your conky you need to save as **gmail.pl** in **~/scripts**.
Create the **scripts** folder in your home directory if you don't have it.
```
#!/usr/bin/perl

# WARNING: Change name and password if posting!!

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="[COLOR="Magenta"]xxxxx[/COLOR]"; #username for gmail account
$pass="[COLOR="#ff00ff"]xxxxx[/COLOR]"; #password for gmail account
$file="/tmp/gmail.html"; #temporary file to store gmail

#wrap format for subject
$Text::Wrap::columns=65; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

#limit the number of emails to be displayed
$emails=4; #if -1 display all emails

&passwd; #give password the proper url character encoding

switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		if ($new>0){
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "Sender: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote."\n";
				print wrap($initial_tab, $subsequent_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	} 	
	case "e" { #print number of new emails, $from, and $subj
		&gmail;
		if($new==0){print "You have no new emails.\n";}
		else{
			print "You have $new new email(s).\n";
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote;
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	}
	else {
		print "Usage Error: gmail.pl <option>\n";
		print "\tn displays number of new emails\n";
		print "\ts displays from line and subject line for each new email.\n";
		print "\te displays the number of new emails and from line plus \n";
		print "\t\tsubject line for each new email.\n";
	} #didn't give proper option
}

sub gmail{
	if(!(-e $file)){ #create file if it does not exists
		`touch $file`;
	} 

	#get new emails
	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom --no-check-certificate> $file`;

	open(IN, $file); #open $file

	my $i=0; #initialize count
	$new=0; #initialize new emails to 0

	my $flag=0;

	while(<IN>){ #cycle through $file
		if(/<entry>/){$flag=1;}
		elsif(/<fullcount>(\d+)<\/fullcount>/){$new=$1;} #grab number of new emails
		elsif($flag==1){ 
			if(/<title>.+<\/title>/){push(@subj, &msg);} #grab new email titles
			elsif(/<name>(.+)<\/name>/){push(@from, $1); $flag=0;} #grab new email from lines
		}
	}

	close(IN); #close $file
}

sub passwd{ #change to url escape codes in password
	#URL ESCAPE CODES
	$_=$pass;
	s/\%/\%25/g;
	s/\#/\%23/g;
	s/\$/\%24/g;
	s/\&/\%26/g;
	s/\//\%2F/g;
	s/\:/\%3A/g;
	s/\;/\%3B/g;
	s/\</\%3C/g;
	s/\=/\%3D/g;
	s/\>/\%3E/g;
	s/\?/\%3F/g;
	s/\@/\%40/g;
	s/\[/\%5B/g;
	s/\\/\%5C/g;
	s/\]/\%5D/g;
	s/\^/\%5E/g;
	s/\`/\%60/g;
	s/\{/\%7B/g;
	s/\|/\%7C/g;
	s/\}/\%7D/g;
	s/\~/\%7E/g;
	$pass=$_;
}

sub msg{
	#THE HTML CODED CHARACTER SET [ISO-8859-1]
	chomp; s/<title>(.+)<\/title>/$1/; #get just the subject
	#now replace any special characters
	s/\&\#33\;/!/g;        #Exclamation mark
	s/\&\#34\;/"/g; s/\&quot\;/"/g;      #Quotation mark
	s/\&\#35\;/#/g;        #Number sign
	s/\&\#36\;/\$/g;        #Dollar sign
	s/\&\#37\;/%/g;        #Percent sign
	s/\&\#38\;/&/g; s/\&amp\;/&/g;        #Ampersand
	s/\&\#39\;/'/g;        #Apostrophe
	s/\&\#40\;/(/g;        #Left parenthesis
	s/\&\#41\;/)/g;        #Right parenthesis
	s/\&\#42\;/*/g;        #Asterisk
	s/\&\#43\;/+/g;        #Plus sign
	s/\&\#44\;/,/g;        #Comma
	s/\&\#45\;/-/g;        #Hyphen
	s/\&\#46\;/./g;        #Period (fullstop)
	s/\&\#47\;/\//g;        #Solidus (slash)
	s/\&\#58\;/:/g;        #Colon
	s/\&\#59\;/\;/g;        #Semi-colon
	s/\&\#60\;/</g; s/\&lt\;/</g;        #Less than
	s/\&\#61\;/=/g;        #Equals sign
	s/\&\#62\;/>/g; s/\&gt\;/>/g;        #Greater than
	s/\&\#63\;/\?/g;        #Question mark
	s/\&\#64\;/\@/g;        #Commercial at
	s/\&\#91\;/\[/g;        #Left square bracket
	s/\&\#92\;/\\/g;        #Reverse solidus (backslash)
	s/\&\#93\;/\]/g;        #Right square bracket
	s/\&\#94\;/\^/g;        #Caret
	s/\&\#95\;/_/g;        #Horizontal bar (underscore)
	s/\&\#96\;/\`/g;        #Acute accent
	s/\&\#123\;/\{/g;        #Left curly brace
	s/\&\#124\;/|/g;        #Vertical bar
	s/\&\#125\;/\}/g;        #Right curly brace
	s/\&\#126\;/~/g;        #Tilde
	s/\&\#161\;/¡/g;        #Inverted exclamation
	s/\&\#162\;/¢/g;        #Cent sign
	s/\&\#163\;/£/g;        #Pound sterling
	s/\&\#164\;/¤/g;        #General currency sign
	s/\&\#165\;/¥/g;        #Yen sign
	s/\&\#166\;/¦/g;        #Broken vertical bar
	s/\&\#167\;/§/g;        #Section sign
	s/\&\#168\;/¨/g;        #Umlaut (dieresis)
	s/\&\#169\;/©/g; s/\&copy\;/©/g;        #Copyright
	s/\&\#170\;/ª/g;        #Feminine ordinal
	s/\&\#171\;/«/g;        #Left angle quote, guillemotleft
	s/\&\#172\;/¬/g;        #Not sign
	s/\&\#174\;/®/g;        #Registered trademark
	s/\&\#175\;/¯/g;        #Macron accent
	s/\&\#176\;/°/g;        #Degree sign
	s/\&\#177\;/±/g;        #Plus or minus
	s/\&\#178\;/²/g;        #Superscript two
	s/\&\#179\;/³/g;        #Superscript three
	s/\&\#180\;/´/g;        #Acute accent
	s/\&\#181\;/µ/g;        #Micro sign
	s/\&\#182\;/¶/g;        #Paragraph sign
	s/\&\#183\;/·/g;        #Middle dot
	s/\&\#184\;/¸/g;        #Cedilla
	s/\&\#185\;/¹/g;        #Superscript one
	s/\&\#186\;/º/g;        #Masculine ordinal
	s/\&\#187\;/»/g;        #Right angle quote, guillemotright
	s/\&\#188\;/¼/g; s/\&frac14\;/¼/g;       # Fraction one-fourth
	s/\&\#189\;/½/g; s/\&frac12\;/½/g;       # Fraction one-half
	s/\&\#190\;/¾/g; s/\&frac34\;/¾/g;       # Fraction three-fourths
	s/\&\#191\;/¿/g;        #Inverted question mark
	s/\&\#192\;/À/g;        #Capital A, grave accent
	s/\&\#193\;/Á/g;        #Capital A, acute accent
	s/\&\#194\;/Â/g;        #Capital A, circumflex accent
	s/\&\#195\;/Ã/g;        #Capital A, tilde
	s/\&\#196\;/Ä/g;        #Capital A, dieresis or umlaut mark
	s/\&\#197\;/Å/g;        #Capital A, ring
	s/\&\#198\;/Æ/g;        #Capital AE dipthong (ligature)
	s/\&\#199\;/Ç/g;        #Capital C, cedilla
	s/\&\#200\;/È/g;        #Capital E, grave accent
	s/\&\#201\;/É/g;        #Capital E, acute accent
	s/\&\#202\;/Ê/g;        #Capital E, circumflex accent
	s/\&\#203\;/Ë/g;        #Capital E, dieresis or umlaut mark
	s/\&\#204\;/Ì/g;        #Capital I, grave accent
	s/\&\#205\;/Í/g;        #Capital I, acute accent
	s/\&\#206\;/Î/g;        #Capital I, circumflex accent
	s/\&\#207\;/Ï/g;        #Capital I, dieresis or umlaut mark   
	s/\&\#208\;/Ð/g;        #Capital Eth, Icelandic
	s/\&\#209\;/Ñ/g;        #Capital N, tilde
	s/\&\#210\;/Ò/g;        #Capital O, grave accent
	s/\&\#211\;/Ó/g;        #Capital O, acute accent
	s/\&\#212\;/Ô/g;        #Capital O, circumflex accent
	s/\&\#213\;/Õ/g;        #Capital O, tilde
	s/\&\#214\;/Ö/g;        #Capital O, dieresis or umlaut mark
	s/\&\#215\;/×/g;        #Multiply sign
	s/\&\#216\;/Ø/g;        #Capital O, slash
	s/\&\#217\;/Ù/g;        #Capital U, grave accent
	s/\&\#218\;/Ú/g;        #Capital U, acute accent
	s/\&\#219\;/Û/g;        #Capital U, circumflex accent
	s/\&\#220\;/Ü/g;        #Capital U, dieresis or umlaut mark
	s/\&\#221\;/Ý/g;        #Capital Y, acute accent
	s/\&\#222\;/Þ/g;        #Capital THORN, Icelandic
	s/\&\#223\;/ß/g;        #Small sharp s, German (sz ligature)
	s/\&\#224\;/à/g;        #Small a, grave accent
	s/\&\#225\;/á/g;        #Small a, acute accent
	s/\&\#226\;/â/g;        #Small a, circumflex accent
	s/\&\#227\;/ã/g;        #Small a, tilde
	s/\&\#228\;/ä/g;        #Small a, dieresis or umlaut mark
	s/\&\#229\;/å/g;        #Small a, ring
	s/\&\#230\;/æ/g;        #Small ae dipthong (ligature)
	s/\&\#231\;/ç/g;        #Small c, cedilla
	s/\&\#232\;/è/g;        #Small e, grave accent
	s/\&\#233\;/é/g;        #Small e, acute accent
	s/\&\#234\;/ê/g;        #Small e, circumflex accent
	s/\&\#235\;/ë/g;        #Small e, dieresis or umlaut mark
	s/\&\#236\;/ì/g;        #Small i, grave accent
	s/\&\#237\;/í/g;        #Small i, acute accent
	s/\&\#238\;/î/g;        #Small i, circumflex accent
	s/\&\#239\;/ï/g;        #Small i, dieresis or umlaut mark
	s/\&\#240\;/ð/g;        #Small eth, Icelandic
	s/\&\#241\;/ñ/g;        #Small n, tilde
	s/\&\#242\;/ò/g;        #Small o, grave accent
	s/\&\#243\;/ó/g;        #Small o, acute accent
	s/\&\#244\;/ô/g;        #Small o, circumflex accent
	s/\&\#245\;/õ/g;        #Small o, tilde
	s/\&\#246\;/ö/g;        #Small o, dieresis or umlaut mark
	s/\&\#247\;/÷/g;        #Division sign
	s/\&\#248\;/ø/g;        #Small o, slash
	s/\&\#249\;/ù/g;        #Small u, grave accent
	s/\&\#250\;/ú/g;        #Small u, acute accent
	s/\&\#251\;/û/g;        #Small u, circumflex accent
	s/\&\#252\;/ü/g;        #Small u, dieresis or umlaut mark
	s/\&\#253\;/ý/g;        #Small y, acute accent
	s/\&\#254\;/þ/g;        #Small thorn, Icelandic
	s/\&\#255\;/ÿ/g;        #Small y, dieresis or umlaut mark
	s/^\s+//;
	return $_;
}
```
[COLOR="#ff00ff"]Add your gmail username and password in highlights.[/COLOR]

Make the script executable(in the terminal)...
```
chmod +x ~/scripts/gmail.pl
```
...and you should be good to go.


> #################
##    GMAIL    ##
##################
${voffset 10}${font [COLOR="Green"]Radis sans[/COLOR]:bold:size=10}${color2}GMAIL ${color8} ${hr 2}
You have ${color yellow}${texeci [COLOR="DarkOrange"]60[/COLOR] perl ~/scripts/gmail.pl n} ${color}new email messages.
${execi [COLOR="#ff8c00"]60[/COLOR] perl ~/scripts/gmail.pl s}
[COLOR="#008000"]Make sure you have this font or change it.[/COLOR]

[COLOR="#ff8c00"]These values set your conky to check for new mail every 60 secs.[/COLOR]
May be a bit short unless you get a lot of emails.
I have mine set at 300.

If you have any problems, post your conky config so I can test it.

---

### Post by Arminius on 2011-03-04
I followed those instructions, to the letter and it hasn't changed from it's deafault, "you have new email messages"
even though I don't have new email messages

---

### Post by stinkeye on 2011-03-04
Test the script is working
Do you get a number on the last line of output when you
run this in terminal.
```
~/scripts/gmail.pl n
``` 

eg my output when I have no emails
```
Resolving mail.google.com... 74.125.237.88
Connecting to mail.google.com|74.125.237.88|:443... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to mail.google.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 348 [text/xml]
Saving to: `STDOUT'

100%[=============================================================================================================================>] 348         --.-K/s   in 0s      

2011-03-05 09:30:58 (14.0 MB/s) - written to stdout [348/348]

0
```


Try the rss feed in your browser to see if it works with...
```
https://[COLOR="Magenta"]username[/COLOR]:[COLOR="#ff00ff"]password[/COLOR]@mail.google.com/mail/feed/atom
```
[COLOR="Magenta"]Insert your username and password.
[/COLOR]

Also do you use any special characters in your username like "**@**" or "**.**"
You would need to escape these characters with a backslash "\".
eg if your username was ```
joe.blow@computer
```
You would need to put it in the gmail.pl script as
```
joe\.blow\@computer
```


Post your complete conky config so I can test.
Using your posted code it works here.

---

### Post by Arminius on 2011-03-13
ok, I put this on pause for a long time, had some problems with conky weather, so I went through those instructions again.
Only this time I got a slightly different result, instead of staying forever on "you have new email" it stays forever on "you have 0 new email"
I enclosed a pic of the desktop

So any advice please?

oh the code I used was ```
#!/usr/bin/perl

# WARNING: Change name and password if posting!!

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="my gmail"; #username for gmail account
$pass="my password"; #password for gmail account
$file="/tmp/gmail.html"; #temporary file to store gmail

#wrap format for subject
$Text::Wrap::columns=65; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

#limit the number of emails to be displayed
$emails=4; #if -1 display all emails

&passwd; #give password the proper url character encoding

switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		if ($new>0){
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "Sender: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote."\n";
				print wrap($initial_tab, $subsequent_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	} 	
	case "e" { #print number of new emails, $from, and $subj
		&gmail;
		if($new==0){print "You have no new emails.\n";}
		else{
			print "You have $new new email(s).\n";
			my $size=@from;
			if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote;
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			$size=@from;
			if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	}
	else {
		print "Usage Error: gmail.pl <option>\n";
		print "\tn displays number of new emails\n";
		print "\ts displays from line and subject line for each new email.\n";
		print "\te displays the number of new emails and from line plus \n";
		print "\t\tsubject line for each new email.\n";
	} #didn't give proper option
}

sub gmail{
	if(!(-e $file)){ #create file if it does not exists
		`touch $file`;
	} 

	#get new emails
	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom --no-check-certificate> $file`;

	open(IN, $file); #open $file

	my $i=0; #initialize count
	$new=0; #initialize new emails to 0

	my $flag=0;

	while(<IN>){ #cycle through $file
		if(/<entry>/){$flag=1;}
		elsif(/<fullcount>(\d+)<\/fullcount>/){$new=$1;} #grab number of new emails
		elsif($flag==1){ 
			if(/<title>.+<\/title>/){push(@subj, &msg);} #grab new email titles
			elsif(/<name>(.+)<\/name>/){push(@from, $1); $flag=0;} #grab new email from lines
		}
	}

	close(IN); #close $file
}

sub passwd{ #change to url escape codes in password
	#URL ESCAPE CODES
	$_=$pass;
	s/\%/\%25/g;
	s/\#/\%23/g;
	s/\$/\%24/g;
	s/\&/\%26/g;
	s/\//\%2F/g;
	s/\:/\%3A/g;
	s/\;/\%3B/g;
	s/\</\%3C/g;
	s/\=/\%3D/g;
	s/\>/\%3E/g;
	s/\?/\%3F/g;
	s/\@/\%40/g;
	s/\[/\%5B/g;
	s/\\/\%5C/g;
	s/\]/\%5D/g;
	s/\^/\%5E/g;
	s/\`/\%60/g;
	s/\{/\%7B/g;
	s/\|/\%7C/g;
	s/\}/\%7D/g;
	s/\~/\%7E/g;
	$pass=$_;
}

sub msg{
	#THE HTML CODED CHARACTER SET [ISO-8859-1]
	chomp; s/<title>(.+)<\/title>/$1/; #get just the subject
	#now replace any special characters
	s/\&\#33\;/!/g;        #Exclamation mark
	s/\&\#34\;/"/g; s/\&quot\;/"/g;      #Quotation mark
	s/\&\#35\;/#/g;        #Number sign
	s/\&\#36\;/\$/g;        #Dollar sign
	s/\&\#37\;/%/g;        #Percent sign
	s/\&\#38\;/&/g; s/\&amp\;/&/g;        #Ampersand
	s/\&\#39\;/'/g;        #Apostrophe
	s/\&\#40\;/(/g;        #Left parenthesis
	s/\&\#41\;/)/g;        #Right parenthesis
	s/\&\#42\;/*/g;        #Asterisk
	s/\&\#43\;/+/g;        #Plus sign
	s/\&\#44\;/,/g;        #Comma
	s/\&\#45\;/-/g;        #Hyphen
	s/\&\#46\;/./g;        #Period (fullstop)
	s/\&\#47\;/\//g;        #Solidus (slash)
	s/\&\#58\;/:/g;        #Colon
	s/\&\#59\;/\;/g;        #Semi-colon
	s/\&\#60\;/</g; s/\&lt\;/</g;        #Less than
	s/\&\#61\;/=/g;        #Equals sign
	s/\&\#62\;/>/g; s/\&gt\;/>/g;        #Greater than
	s/\&\#63\;/\?/g;        #Question mark
	s/\&\#64\;/\@/g;        #Commercial at
	s/\&\#91\;/\[/g;        #Left square bracket
	s/\&\#92\;/\\/g;        #Reverse solidus (backslash)
	s/\&\#93\;/\]/g;        #Right square bracket
	s/\&\#94\;/\^/g;        #Caret
	s/\&\#95\;/_/g;        #Horizontal bar (underscore)
	s/\&\#96\;/\`/g;        #Acute accent
	s/\&\#123\;/\{/g;        #Left curly brace
	s/\&\#124\;/|/g;        #Vertical bar
	s/\&\#125\;/\}/g;        #Right curly brace
	s/\&\#126\;/~/g;        #Tilde
	s/\&\#161\;/¡/g;        #Inverted exclamation
	s/\&\#162\;/¢/g;        #Cent sign
	s/\&\#163\;/£/g;        #Pound sterling
	s/\&\#164\;/¤/g;        #General currency sign
	s/\&\#165\;/¥/g;        #Yen sign
	s/\&\#166\;/¦/g;        #Broken vertical bar
	s/\&\#167\;/§/g;        #Section sign
	s/\&\#168\;/¨/g;        #Umlaut (dieresis)
	s/\&\#169\;/©/g; s/\&copy\;/©/g;        #Copyright
	s/\&\#170\;/ª/g;        #Feminine ordinal
	s/\&\#171\;/«/g;        #Left angle quote, guillemotleft
	s/\&\#172\;/¬/g;        #Not sign
	s/\&\#174\;/®/g;        #Registered trademark
	s/\&\#175\;/¯/g;        #Macron accent
	s/\&\#176\;/°/g;        #Degree sign
	s/\&\#177\;/±/g;        #Plus or minus
	s/\&\#178\;/²/g;        #Superscript two
	s/\&\#179\;/³/g;        #Superscript three
	s/\&\#180\;/´/g;        #Acute accent
	s/\&\#181\;/µ/g;        #Micro sign
	s/\&\#182\;/¶/g;        #Paragraph sign
	s/\&\#183\;/·/g;        #Middle dot
	s/\&\#184\;/¸/g;        #Cedilla
	s/\&\#185\;/¹/g;        #Superscript one
	s/\&\#186\;/º/g;        #Masculine ordinal
	s/\&\#187\;/»/g;        #Right angle quote, guillemotright
	s/\&\#188\;/¼/g; s/\&frac14\;/¼/g;       # Fraction one-fourth
	s/\&\#189\;/½/g; s/\&frac12\;/½/g;       # Fraction one-half
	s/\&\#190\;/¾/g; s/\&frac34\;/¾/g;       # Fraction three-fourths
	s/\&\#191\;/¿/g;        #Inverted question mark
	s/\&\#192\;/À/g;        #Capital A, grave accent
	s/\&\#193\;/Á/g;        #Capital A, acute accent
	s/\&\#194\;/Â/g;        #Capital A, circumflex accent
	s/\&\#195\;/Ã/g;        #Capital A, tilde
	s/\&\#196\;/Ä/g;        #Capital A, dieresis or umlaut mark
	s/\&\#197\;/Å/g;        #Capital A, ring
	s/\&\#198\;/Æ/g;        #Capital AE dipthong (ligature)
	s/\&\#199\;/Ç/g;        #Capital C, cedilla
	s/\&\#200\;/È/g;        #Capital E, grave accent
	s/\&\#201\;/É/g;        #Capital E, acute accent
	s/\&\#202\;/Ê/g;        #Capital E, circumflex accent
	s/\&\#203\;/Ë/g;        #Capital E, dieresis or umlaut mark
	s/\&\#204\;/Ì/g;        #Capital I, grave accent
	s/\&\#205\;/Í/g;        #Capital I, acute accent
	s/\&\#206\;/Î/g;        #Capital I, circumflex accent
	s/\&\#207\;/Ï/g;        #Capital I, dieresis or umlaut mark   
	s/\&\#208\;/Ð/g;        #Capital Eth, Icelandic
	s/\&\#209\;/Ñ/g;        #Capital N, tilde
	s/\&\#210\;/Ò/g;        #Capital O, grave accent
	s/\&\#211\;/Ó/g;        #Capital O, acute accent
	s/\&\#212\;/Ô/g;        #Capital O, circumflex accent
	s/\&\#213\;/Õ/g;        #Capital O, tilde
	s/\&\#214\;/Ö/g;        #Capital O, dieresis or umlaut mark
	s/\&\#215\;/×/g;        #Multiply sign
	s/\&\#216\;/Ø/g;        #Capital O, slash
	s/\&\#217\;/Ù/g;        #Capital U, grave accent
	s/\&\#218\;/Ú/g;        #Capital U, acute accent
	s/\&\#219\;/Û/g;        #Capital U, circumflex accent
	s/\&\#220\;/Ü/g;        #Capital U, dieresis or umlaut mark
	s/\&\#221\;/Ý/g;        #Capital Y, acute accent
	s/\&\#222\;/Þ/g;        #Capital THORN, Icelandic
	s/\&\#223\;/ß/g;        #Small sharp s, German (sz ligature)
	s/\&\#224\;/à/g;        #Small a, grave accent
	s/\&\#225\;/á/g;        #Small a, acute accent
	s/\&\#226\;/â/g;        #Small a, circumflex accent
	s/\&\#227\;/ã/g;        #Small a, tilde
	s/\&\#228\;/ä/g;        #Small a, dieresis or umlaut mark
	s/\&\#229\;/å/g;        #Small a, ring
	s/\&\#230\;/æ/g;        #Small ae dipthong (ligature)
	s/\&\#231\;/ç/g;        #Small c, cedilla
	s/\&\#232\;/è/g;        #Small e, grave accent
	s/\&\#233\;/é/g;        #Small e, acute accent
	s/\&\#234\;/ê/g;        #Small e, circumflex accent
	s/\&\#235\;/ë/g;        #Small e, dieresis or umlaut mark
	s/\&\#236\;/ì/g;        #Small i, grave accent
	s/\&\#237\;/í/g;        #Small i, acute accent
	s/\&\#238\;/î/g;        #Small i, circumflex accent
	s/\&\#239\;/ï/g;        #Small i, dieresis or umlaut mark
	s/\&\#240\;/ð/g;        #Small eth, Icelandic
	s/\&\#241\;/ñ/g;        #Small n, tilde
	s/\&\#242\;/ò/g;        #Small o, grave accent
	s/\&\#243\;/ó/g;        #Small o, acute accent
	s/\&\#244\;/ô/g;        #Small o, circumflex accent
	s/\&\#245\;/õ/g;        #Small o, tilde
	s/\&\#246\;/ö/g;        #Small o, dieresis or umlaut mark
	s/\&\#247\;/÷/g;        #Division sign
	s/\&\#248\;/ø/g;        #Small o, slash
	s/\&\#249\;/ù/g;        #Small u, grave accent
	s/\&\#250\;/ú/g;        #Small u, acute accent
	s/\&\#251\;/û/g;        #Small u, circumflex accent
	s/\&\#252\;/ü/g;        #Small u, dieresis or umlaut mark
	s/\&\#253\;/ý/g;        #Small y, acute accent
	s/\&\#254\;/þ/g;        #Small thorn, Icelandic
	s/\&\#255\;/ÿ/g;        #Small y, dieresis or umlaut mark
	s/^\s+//;
	return $_;
}
```

---

### Post by Arminius on 2011-03-13
sorry stinkeye your post only popped up right after I posted just 5 mins ago.
Ok
when I ran ```
~/scripts/gmail.pl n
```
it returned with ```
me@computer:~$ ~/scripts/gmail.pl n
--2011-03-14 09:33:20--  https://myemail:*password*@mail.google.com/mail/feed/atom
Resolving mail.google.com... 74.125.237.23, 74.125.237.24, 74.125.237.21, ...
Connecting to mail.google.com|74.125.237.23|:443... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to mail.google.com:443.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
0

```
hmmm I should mention, I changed the myemail part from my real email, but *password* was exactly as it was? is that ment to happen?

when I put this in terminal ```
https://username:password@mail.google.com/mail/feed/atom
```

it came back with the correct email features.

and no my email doesn't have any weird characters in the part before @

one this that may or may not be relevant, in the part of gmail.pl that contains ```
$user="mygmail5@gmail.com"; #username for gmail account
```
all my email is pink except for @gmail which is green, is that ment to happen?

---

### Post by stinkeye on 2011-03-13
> $user="mygmail5**@gmail.com**"; #username for gmail account

all my email is pink except for @gmail which is green, is that ment to happen?

Your username should not include the **@gmail.com** part.

---

### Post by Arminius on 2011-03-14
that's worked perfectly stinkeye, thanks

---

