---
title: "Conky Gmail Revisited"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by lvleph on 2008-01-27
The conky gmail scripts that I have come across either only gave me the number of new emails or was a bit kludgey. In fact, the one I was using stopped working. So, I decided to write a new script that would be a little more graceful and would not have some of the same issues as the others, like not allowing certain characters in passwords without requiring the user to know url escape codes. Additionally, I have made this version display all html character codes correctly (as long as the font used allows that character). I hope everyone likes it.

**Step 1:** Save the following script in a file named **gmail.pl** and place it in **~/scripts** (/home/<username>/scripts/) folder.

```
#!/usr/bin/perl

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="username"; #username for gmail account
$pass="password"; #password for gmail account
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
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote."\n";
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
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

The usage of the **weather.pl** script above is as follows (also see: Step 4)
```
gmail.pl <option>
        n displays number of new emails
        s displays from line and subject line for each new email.
        e displays the number of new emails and from line plus 
                subject line for each new email.

```

The following will display the number of new emails and who they are from, plus their subjects.
```
./gmail.pl e
```

The following will display just the number of new emails.
```
./gmail.pl n
```

The following will display the from and subject lines of each new email
```
./gmail.pl s
```

The formatting of the subject can be changed by playing with the following variables (lines 13-16):
$Text::Wrap::columns=65; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

The number following $Text::Wrap::columns is the number of columns before wrapping to the next line.
A \t represents one tab.
\" represents a quotation mark.

**Step 2:** Make **gmail.pl** executable.
```
sudo chmod a+x ~/scripts/gmail.pl
```

The script will make a file containing the html code from gmail.com.

**Step 3:** Set $user (line 7) to your user name by replacing <username> with your user name. And then set $pass (line 8 ) to your password by replacing <password> with your password.

**NOTE:** If you have an @ or $ in your password, that symbol needs to be escaped using \. For example if your password is @1234 then when entering your password you need to type \@1234.

**Step 4:**Add the following code to your **conkyrc** file
```
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).
${execi 60 perl ~/scripts/gmail.pl s}
```

If you don't want the number of emails in a different color just use the following
```
${execi 60 perl ~/scripts/gmail.pl e}
```
This will result in once less script run and may be better for someone with a slow computer.

Or if you just want the number of emails.
```
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).
```

The number after each execi represents the number of seconds between each run. So if you want your email checked every 5 mins the number should be 300.

**Step 5:** Avoid certificate errors by ```
sudo apt-get install ca-certificates
```

**UPDATE 28 January 2008:** Added & quot to list of html character encoding.
**UPDATE 29 January 2008:** Added sudo apt-get install ca-certificates in instructions to get rid of certificate error
**UPDATE 04 February 2008:** Added text wrapping for the subjects, and added the ability to limit the number of emails displayed.
**UPDATE 24 February 2008:** Fixed issue with subjects and authors not matching, when new email was part of conversation.

---

### Post by aonegodman on 2008-01-28
Thanks LVLEPH,  and here's a shot of my conky with Gmail notification.   :)

):P

---

### Post by lvleph on 2008-01-28
Just added & quot to character encoding.

---

### Post by ScottKidder on 2008-01-29
--05:42:56--  [https://scott.kidder11:*password*@mail.google.com/mail/feed/atom](https://scott.kidder11:*password*@mail.google.com/mail/feed/atom)
           => `-'
Resolving mail.google.com... 72.14.223.19, 72.14.223.83, 72.14.223.18
Connecting to mail.google.com|72.14.223.19|:443... connected.
WARNING: Certificate verification error for mail.google.com: unable to get local issuer certificate
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [ <=>                                                                                                              ] 885           --.--K/s

05:42:56 (17.51 MB/s) - `-' saved [885]


I get that output in the terminal constantly, which wouldn't be a problem except it generates annoying, extra, constant network traffic. Any ideas?

EDIT:
I fixed it with sudo apt-get install ca-certificates

---

### Post by Meyithi on 2008-01-29
This is fantastic - many thanks.

My conky looks like[ this!]("http://ubuntuforums.org/showpost.php?p=4228922&postcount=1303")

---

### Post by lvleph on 2008-01-29
Okay, I will add the ca-certificates to the instructions. Thank you for that.

I will add the ability to limit the number of emails displayed soon.

---

### Post by kosak on 2008-01-30
My pic again!

---

### Post by lvleph on 2008-02-02
I added some features:
1. Text wrap for long subjects; the formatting for this is on lines 12-16
2. Limit the number of emails displayed; this feature is on line 19 and is currently set to 4, but can be set to off (-1).

Please feel free to beta test and post any problems here. In a few days I will move it to the original directions.

```
#!/usr/bin/perl

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="<username>"; #username for gmail account
$pass="<password>"; #password for gmail account
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
		my $size=@from;
		if ($emailss!=-1 && $size>$emails){$size=$emailss;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			print "From: $from[$i]\n"; #print from line
			$text=$quote.$subj[$i].$quote;
			print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
		}
		print "\n";
		$size=@from;
		if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
	} 	
	case "e" { #print number of new emails, $from, and $subj
		&gmail;
		if($new==0){print "You have no new emails.\n";}
		else{
			print "You have $new new email(s).\n";
			my $size=@from;
			if ($emailss!=-1 && $size>$emails){$size=$emailss;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote;
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			print "\n";
			$size=@from;
			if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	}
	else {
		print "Usage Error: gmail.pl <option>
\tn displays number of new emails
\ts displays from line and subject line for each new email.
\te displays the number of new emails and from line plus \n\t\tsubject line for each new email.\n";
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
			elsif(/<name>(.+)<\/name>/){push(@from, $1);} #grab new email from lines
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

### Post by lvleph on 2008-02-03
Found an issue with the from and subject lines not being seperated, so I fixed it.

```
#!/usr/bin/perl

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="<username>"; #username for gmail account
$pass="<password>"; #password for gmail account
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
		my $size=@from;
		if ($emailss!=-1 && $size>$emails){$size=$emailss;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			print "From: $from[$i]\n"; #print from line
			$text=$quote.$subj[$i].$quote."\n";
			print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
		}
		print "\n";
		$size=@from;
		if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
	} 	
	case "e" { #print number of new emails, $from, and $subj
		&gmail;
		if($new==0){print "You have no new emails.\n";}
		else{
			print "You have $new new email(s).\n";
			my $size=@from;
			if ($emailss!=-1 && $size>$emails){$size=$emailss;} #limit number of emails displayed
			for(my $i=0; $i<$size; ++$i){
				print "From: $from[$i]\n"; #print from line
				$text=$quote.$subj[$i].$quote;
				print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
			}
			print "\n";
			$size=@from;
			if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	}
	else {
		print "Usage Error: gmail.pl <option>
\tn displays number of new emails
\ts displays from line and subject line for each new email.
\te displays the number of new emails and from line plus \n\t\tsubject line for each new email.\n";
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
			elsif(/<name>(.+)<\/name>/){push(@from, $1);} #grab new email from lines
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

### Post by lvleph on 2008-02-04
Update to latest version which includes text wrapping for subjects and allows more control over formatting of subject lines.

---

### Post by aonegodman on 2008-02-05
Is there a way to set the time delay between mail checks. Mine seems to check every minute.  Thanks.

I think I just figured it out by changing the numerical value after texeci.  Right?

```

${texeci **300** perl ~/scripts/gmail.pl n}

```

:)

---

### Post by lvleph on 2008-02-05
Just change that number supposedly that number represents the number of seconds.

---

### Post by Nythain on 2008-02-12
segmentation faulting out the wazzu
any clue...

EDIT: Rebooting allowed it to load up... guess i had something wrong, and conky was very confused for a while... oh well, working now... thanks for the great scripts... i think i like this one better than the weather (wich i like more than sliced cheese)

---

### Post by lvleph on 2008-02-12
I don't know what the issue would be. I have noticed that the display of new emails out of new emails is not displaying the correct total number of emails.

---

### Post by lvleph on 2008-02-13
I have been looking over my script, and I connot figure out why the total number in the out of portion is one off. When I have 5 emails it is correct, but once I have 6 emails it is no longer correct. I am lost.

---

### Post by likeatim on 2008-02-19
thanks for that script, i'm using it now.
however, I'd like to have sender and subject in one row, so i changed case "s" to the following:
```
switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		my $size=@from;
		if ($emailss!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			print "- $from[$i]:$text$quote$subj[$i]$quote\n"; #print from line
			#$text=$quote.$subj[$i].$quote."\n";
			print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
		}
		print "\n";
		$size=@from;
		if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
	} 	

```
However, very often subject and sender don't match. as an example, i get 3 emails. 
the script will show me this:
sender 1: subject 2
sender 2: subject 3
sender 3: no subject
what am i doing wrong?

Also: is it possible to have differendt colours for sender and subject? I tried to put conky colour codes into the pl script, but that didn't work out....
2

---

### Post by lvleph on 2008-02-19
> **likeatim said:**
> thanks for that script, i'm using it now.
however, I'd like to have sender and subject in one row, so i changed case "s" to the following:
```
switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		my $size=@from;
		if ($emailss!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			print "- $from[$i]:$text$quote$subj[$i]$quote\n"; #print from line
			#$text=$quote.$subj[$i].$quote."\n";
			print wrap($initial_tab, $subsequent_tab, $text); #print subject with word wrap
		}
		print "\n";
		$size=@from;
		if ($emailss!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
	} 	

```
However, very often subject and sender don't match. as an example, i get 3 emails. 
the script will show me this:
sender 1: subject 2
sender 2: subject 3
sender 3: no subject
what am i doing wrong?

Also: is it possible to have differendt colours for sender and subject? I tried to put conky colour codes into the pl script, but that didn't work out....
2
I see the issue. You are printing two different subjects that I can see. You need to comment out the print wrap line. Also, the code you are using is the old code and still has some errors in it. Grab the newest version and make your changes from there.

In fact, a better way to do it so that you can take advantage of text wrapping would be to comment out the from line and change the $text line to the following:
```
$text=$from[$i].":".$quote.$subj[$i].$quote."\n";
```

As far as changing colors of the from and the subj. You would have to have that sent out in two different script calls. Conky can't change the color of parts of a scrip output.

---

### Post by lvleph on 2008-02-21
Okay, so the problem with there being the wrong from on a subj has to do with the way gmail reports new emails. I didn't realize they report the from for the entire conversation. I will have to fix that, but I have midterms this week, so I will fix it when I have a chance.

---

### Post by lvleph on 2008-02-24
Okay, I have fixed the issue with the subjects and from not corresponding. The issue was with gmails use of conversations. I didn't take into account that it lists multiple authors.

---

### Post by likeatim on 2008-02-24
thanks!
works fine now!

---

### Post by likeatim on 2008-02-25
I changed some of the script for my needs. I'm managing 3 Gmail accounts with it

[[IMG]http://img245.imageshack.us/img245/7288/conkydp6.th.png[/IMG]](http://img245.imageshack.us/my.php?image=conkydp6.png)

_.conkyrc:_
```
${color #ddaa00}Gmail1:${texeci 240 perl ~/.conky/gmail1.pl n}${alignc}${color #009bf9}Gmail2: ${texeci 240 perl ~/.conky/gmail2.pl n}${alignr}${color gray}Gmail3:${texeci 240 perl ~/.conky/gmail3.pl n}
${color #ddaa00}${texeci 240 perl ~/.conky/gmail1.pl s}
${color #009bf9}${texeci 240 perl ~/.conky/gmail2.pl s}
${color gray}${texeci 240 perl ~/.conky/gmail3.pl s}
```
This will show the number of new emails for each account in one row.

**[COLOR="Red"]Q: How do I align these 3 properly? See the attached screenshot[/COLOR]**


_gmail.pl_
```
#!/usr/bin/perl

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="username"; #username for gmail account
$pass="password"; #password for gmail account
**[COLOR="Blue"]$file="~/.conky/gmail1.html";[/COLOR]** #temporary file to store gmail

#wrap format for subject
$Text::Wrap::columns=48; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

#limit the number of emails to be displayed
$emails=-1; #if -1 display all emails

&passwd; #give password the proper url character encoding

switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		if ($new>0){
		my $size=@from;
		if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			$text=[COLOR="Red"]**".\ ".**[/COLOR]$from[$i].":".$quote.$subj[$i].$quote."\n";
			#$text=$quote.$subj[$i].$quote."\n";
			#$from[$i]:$text$quote$subj[$i]$quote\n"; print from line
			print wrap($initial_tab, $subsequent_tab, [COLOR="Red"]**$i+1**[/COLOR],$text); #print subject with word wrap
		}
		$size=@from;
		if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	} 	

```
[COLOR="Red"]Red Code[/COLOR]: This way, it will show a counter in front of the emails, which makes it easier for me to get an overview. 
[COLOR="Blue"]Blue code:[/COLOR] I think it's safer to store the Gmail temp files in the home directory. This way, other users can't read it, and if your home partition is encrypted (like mine), it makes more sense like this.

Thanks again for the original script!

---

### Post by lvleph on 2008-02-25
> **likeatim said:**
> I changed some of the script for my needs. I'm managing 3 Gmail accounts with it

[[IMG]http://img257.imageshack.us/img257/1046/conkynz7.th.png[/IMG]](http://img257.imageshack.us/my.php?image=conkynz7.png)

_.conkyrc:_
```
${color #ddaa00}Gmail1:${texeci 240 perl ~/.conky/gmail1.pl n}${alignc}${color #009bf9}Gmail2: ${texeci 240 perl ~/.conky/gmail2.pl n}${alignr}${color gray}Gmail3:${texeci 240 perl ~/.conky/gmail3.pl n}
${color #ddaa00}${texeci 240 perl ~/.conky/gmail1.pl s}
${color #009bf9}${texeci 240 perl ~/.conky/gmail2.pl s}
${color gray}${texeci 240 perl ~/.conky/gmail3.pl s}
```
This will show the number of new emails for each account in one row.

**[COLOR="Red"]Q: How do I align these 3 properly? See the attached screenshot[/COLOR]**


_gmail.pl_
```
#!/usr/bin/perl

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="username"; #username for gmail account
$pass="password"; #password for gmail account
**[COLOR="Blue"]$file="~/.conky/gmail1.html";[/COLOR]** #temporary file to store gmail

#wrap format for subject
$Text::Wrap::columns=48; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

#limit the number of emails to be displayed
$emails=-1; #if -1 display all emails

&passwd; #give password the proper url character encoding

switch($what){ #determine what the user wants
	case "n" {&gmail; print "$new\n";} #print number of new emails
	case "s" { #print $from and $subj for new email
		&gmail;
		if ($new>0){
		my $size=@from;
		if ($emails!=-1 && $size>$emails){$size=$emails;} #limit number of emails displayed
		for(my $i=0; $i<$size; ++$i){
			$text=[COLOR="Red"]**".\ ".**[/COLOR]$from[$i].":".$quote.$subj[$i].$quote."\n";
			#$text=$quote.$subj[$i].$quote."\n";
			#$from[$i]:$text$quote$subj[$i]$quote\n"; print from line
			print wrap($initial_tab, $subsequent_tab, [COLOR="Red"]**$i+1**[/COLOR],$text); #print subject with word wrap
		}
		$size=@from;
		if ($emails!=-1 && $size >$emails){print "$emails out of $size new emails displayed\n";}
		}
	} 	

```
[COLOR="Red"]Red Code[/COLOR]: This way, it will show a counter in front of the emails, which makes it easier for me to get an overview. 
[COLOR="Blue"]Blue code:[/COLOR] I think it's safer to store the Gmail temp files in the home directory. This way, other users can't read it, and if your home partition is encrypted (like mine), it makes more sense like this.

Thanks again for the original script!

I store it in the temp directory so that it is deleted when you computer is shut down, but I see your point about security. I could delete the file when done. Or I could just not use a temp file. I just haven't figured out how to read all the data from memory.

---

### Post by Melchmon360 on 2008-03-04
Thank you for making and wonderful script. I started useing and abusing conky because of it.

---

### Post by Maelgwyn on 2008-03-04
Because my password has an @ symbol in it, it seems to be confusing the gmail.pl script. Is there a way around this? I'd rather not change my email if I can help it... :)

---

### Post by lvleph on 2008-03-04
It shouldn't. What is happening? I wrote it specifically to take into account symbols like that in passwords.

---

### Post by Maelgwyn on 2008-03-04
well in the gmail.pl script, the password is underlined (I'm using Gedit). And the actual conky screen shows 0 email even when I know full well there are emails! I set the refresh time to 15 (it's in seconds isn't it?)...

---

### Post by Joeb454 on 2008-03-04
you might want to see if you can escape the @ sign

What happens if you put a \ in front of it (a backslash, in case you couldn't read it :))?

---

### Post by lvleph on 2008-03-05
Escaping the @ will not do anything. I have it coded to handle @. Try running the gmail.pl in terminal and tell me the output. I have not heard of anyone else having this problem. If you were not able to log in it wouldn't even show that you had zero emails.

I specifically tested the @, because of the way perl handles those. I know for sure that there is no problem with having a @ in your password. Anyway, run the script in the terminal and let me know what it says.

Also, it only tells you the number of new emails. Not how many emails you have overall. I just wanted to make sure that was clear.

---

### Post by Maelgwyn on 2008-03-05
Yeah, I was aware that it would only show new emails...


Sorry - I'm a complete noob. I was putting my username & password AFTER the # and not in the "<>"

*blush*

All sorted now

---

### Post by lvleph on 2008-03-05
It would have been weird if you were the first to have this problem. Good to see that you worked it out.

Oh and here is a [present](http://www.yougotrickrolled.com/).

---

### Post by Maelgwyn on 2008-03-06
Bah - still having isssues:
```
nik@taonga:~/scripts$ ./gmail.pl n
--08:40:33--  https://cerddorion:*password*@mail.google.com/mail/feed/atom
           => `-'
Resolving mail.google.com... 74.125.19.83, 74.125.19.17, 74.125.19.19, ...
Connecting to mail.google.com|74.125.19.83|:443... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
0

```

---

### Post by lvleph on 2008-03-06
Make sure that all you have are the quotation marks and your password between them. There should not be any of the <password>.

---

### Post by Maelgwyn on 2008-03-06
That was the first thing I checked... >.<

---

### Post by lvleph on 2008-03-06
Make sure you are only including your user name that is everything before the @gmail.com. So if your email was [email]example@gmail.com[/email], you would have
```
$user="example";
```
For the password; say your pass was 1235@678 you would have
```
$pass="1235@678";
```

If you have that all correct, I am going to have to look into some things.

---

### Post by lvleph on 2008-03-06
Okay, I figured out the issue. In front of the @ place a \.
So if your pass is @1234 you should have
```
$pass="\@1234";
```

I will have to find a workaround for this that is easier on the user.

---

### Post by Maelgwyn on 2008-03-06
I've got an @ near the middle of my password, will this escape everything else as well?

I can't check now as I'm at work, and IT won't let me have my own ssh connection to home :P

---

### Post by lvleph on 2008-03-07
The escape just tells perl that it is a character and not an operator. So, no it only works on one character at a time.

---

### Post by Maelgwyn on 2008-03-07
Sweet - that's done it :D

---

### Post by Roofie on 2008-03-15
Thanx this works good :KS

---

### Post by NewProggie on 2008-03-16
Hi,

I don't know, I've tried hard for hours now to get the conky-script working, but it's still giving me an 401 error, everytime the wget-command tries to connect to gmail.

A simple test on the shell with following command gave me this:

```
wget -O - https://john.smith:topsecret@mail.google.com/mail/feed/atom
```

output:

--13:24:24--  [https://john.smith:*password*@mail.google.com/mail/feed/atom/](https://john.smith:*password*@mail.google.com/mail/feed/atom/)
           => `-'
AuflÃ¶sen des Hostnamen Â»mail.google.comÂ«.... 72.14.221.19, 72.14.221.17, 72.14.221.83, ...
Verbindungsaufbau zu mail.google.com|72.14.221.19|:443... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 401 Unauthorized
Authorisierung fehlgeschlagen.


Can anybody tell me where is my mistake?

thanks in regard

---

### Post by lvleph on 2008-03-16
It looks like you are having a password issue?

---

### Post by Stalafin on 2008-03-16
Is there a way to have several accounts taken care of by this script? I could create a new instance of course...

Did you think about transfering username and password into conky, so that this info would be handled by conky, calling the script with those arguments?

---

### Post by likeatim on 2008-03-17
> **Stalafin said:**
> Is there a way to have several accounts taken care of by this script? I could create a new instance of course...
see this post in this thread: [http://ubuntuforums.org/showpost.php?p=4401543&postcount=21](http://ubuntuforums.org/showpost.php?p=4401543&postcount=21)
just create another perl file and point to it in conky...

---

### Post by NewProggie on 2008-03-17
> **lvleph said:**
> It looks like you are having a password issue?

Hello,

unfortunately not:-(

If I'm typing this string ([https://user.name:pass@mail.google.com/mail/feed/atom](https://user.name:pass@mail.google.com/mail/feed/atom))
into my browser (Firefox)then it's working.

I have absolutely no idea what else I might should check :confused:

---

### Post by lvleph on 2008-03-17
> **NewProggie said:**
> Hello,

unfortunately not:-(

If I'm typing this string ([https://user.name:pass@mail.google.com/mail/feed/atom](https://user.name:pass@mail.google.com/mail/feed/atom))
into my browser (Firefox)then it's working.

I have absolutely no idea what else I might should check :confused:

Do you have special characters in you password. Maybe an esset? If so that would be a problem. I am did not take into account non-english characters.

---

### Post by NewProggie on 2008-03-17
> **lvleph said:**
> Do you have special characters in you password. Maybe an esset? If so that would be a problem. I am did not take into account non-english characters.

No, just letters and Numbers.
I've already read through the whole thread to eliminate other possible problems.
The thing is that it's working, if I put it directly into the browser.. Really wired, but I keep searching for the mistake I'm doing (or maybe it's a matter of my setup here, I don't know)

---

### Post by lvleph on 2008-03-17
Put in some bogus information for your username and password and post the script here. I think I might update the script to have the username and password as an input.

---

### Post by NewProggie on 2008-03-17
Ok,

here's the script I'm using

```
import os
import string
import sys
import time

#Enter your username and password below within double quotes
# eg. username="username" and password="password"

username="john.smith"
password="T0ps3cret"

filename="/home/yourusername/scripts/conky-gmail-new" #just change path, ie /home/yourusername/scripts/conky-gmail-new

emails=0
argument=sys.argv[1]

if (argument=="check"):

   com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"
   temp=os.popen(com)
   msg=temp.read()
   index=string.find(msg,"<fullcount>")
   index2=string.find(msg,"</fullcount>")
   fc=int(msg[index+11:index2])

   if (int(fc)==0):
      if os.path.exists(filename):
         os.remove(filename)
   else:
      file = open(filename, "w")
      if (int(fc)==1):
         file.write("1 new email")
      else:
         file.write(str(fc)+" new emails")
      file.close

elif (argument=="read"):

   time.sleep(1)

   if os.path.exists(filename):
      file = open(filename, "r")
      emails = file.read()
      file.close()
   print emails
```

Thanks in advance

---

### Post by lvleph on 2008-03-17
I wonder if it might have something to capitalization. Try to make your password only have lower case letters and see if it works. I thought I tested that, but maybe not.

The other thing you might want to try is escaping the period in your user name so "john.smith" would be "john\.smith".

---

### Post by NewProggie on 2008-03-18
Well,

thanks for your patience.

I will try this later in a few, I'm at work at the moment

---

### Post by NewProggie on 2008-03-18
Thanks,

now it's working, even though I didn't change anything.

I guess, last time, I tried it so often in a very short time period, that google may closed the connection from my ip adress for a limited time. At least, this is my only suggestion.

---

### Post by Stefan_xfce on 2008-03-22
Thanks a lot, here's a screenshot of my conky:
[IMG]http://img27.picoodle.com/img/img27/4/3/22/t_asddddm_6fe84a7.jpg[/IMG]
Large:
[http://img27.picoodle.com/img/img27/4/3/22/f_asddddm_6fe84a7.jpg]("http://img27.picoodle.com/img/img27/4/3/22/f_asddddm_6fe84a7.jpg")

What about security, isn't it a bit unsafe, to have a non encrypted file with your gmail password in it?

---

### Post by Kiri on 2008-03-31
> **Stefan_xfce said:**
> 
What about security, isn't it a bit unsafe, to have a non encrypted file with your gmail password in it?

I'm wondering about this too... And about how it passes the information to gmail. Is there any chance it might be seen by a 3rd party?

---

### Post by lvleph on 2008-04-03
I am not sure.

---

### Post by starryeyedboy on 2008-04-18
> **lvleph said:**
> Okay, I figured out the issue. In front of the @ place a \.
So if your pass is @1234 you should have
```
$pass="\@1234";
```

I will have to find a workaround for this that is easier on the user.

thanks for that. i had a similar issue. in my password, i use "\" . to solve my problem, i had to type "\\" for every "\" in my password. cheers =)

---

### Post by djpate on 2008-04-29
Thanks for this great script but i'm experiencing issue with it.

It seems to work but on the 3rd email it stops.

Check out the screenshot to get a better idea

**[[IMG]http://img258.imageshack.us/img258/8196/capturefl5.th.png[/IMG]](http://img258.imageshack.us/my.php?image=capturefl5.png)**

I don't know how to fix this

---

### Post by lvleph on 2008-04-29
I don't know what the issue is. I have never had it and no one else has had that issue either.

---

### Post by ragingmon on 2008-05-21
> **djpate said:**
> Thanks for this great script but i'm experiencing issue with it.

It seems to work but on the 3rd email it stops.

Check out the screenshot to get a better idea

**[[IMG]http://img258.imageshack.us/img258/8196/capturefl5.th.png[/IMG]](http://img258.imageshack.us/my.php?image=capturefl5.png)**

I don't know how to fix this
I also had this issue. 
I also tried conky+gcalcli and the issue also occurs. It's like its limits characters. 

any help out here?

---

### Post by lvleph on 2008-05-21
Try changing $emails=4; to $emails=-1; , in the script, and see if that changes things.

---

### Post by ragingmon on 2008-05-21
> **lvleph said:**
> Try changing $emails=4; to $emails=-1; , in the script, and see if that changes things.

Finally I got it. 
just adding the **text_buffer_size** in the conkyrc

```
text_buffer_size 1000
```

darn, this is the result of too much googling, thanks to [[COLOR="Red"]this post.[/COLOR]]("http://bbs.archlinux.org/viewtopic.php?id=48455")

---

### Post by lvleph on 2008-05-21
I just ran it from command line and it worked just fine, so it must be the text buffer size like you said.

---

### Post by ioio82 on 2008-05-24
what do i have to do with an error like this?

 wget -O - [https://censored:censored\@mail.google.com/mail/feed/atom](https://censored:censored\@mail.google.com/mail/feed/atom) --no-check-certificate
[https://censored:censored@mail.google.com/mail/feed/atom:](https://censored:censored@mail.google.com/mail/feed/atom:) Bad port number.

---

### Post by jba6511 on 2008-05-27
thanks for the script. I was also having password issues due to the @ and $ characters. Escaping with the \ in front of each character resolved the problem.

---

### Post by symera on 2008-06-08
I hope this isn't a foolish question, but perl doesn't seem to like my script. I've just copied the code from the first post and put in my username and password.

When I run:
```
perl ~/scripts/gmail.pl
```

I get:

```
Backticks found where operator expected at gmail.pl line 70, near "sudo 
	#get new emails
	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom --no-check-certificate> $file`"
	(Do you need to predeclare sudo?)
syntax error at gmail.pl line 70, near "sudo 
	#get new emails
	`wget -O - https://$user:$pass\@mail.google.com/mail/feed/atom --no-check-certificate> $file`"
Execution of gmail.pl aborted due to compilation errors.

```

Does anyone know what I've done wrong?
-r

---

### Post by HighInBC on 2008-07-13
Call me crazy, but instead of scraping a feed I just use gmail's wonderful IMAP interface. This simple script gets the sender, subject, and time of each unread message in the inbox and can be ran with a maximum:

Do: sudo apt-get install libmail-imapclient-perl

```
#!/usr/bin/perl
use Mail::IMAPClient;
use IO::Socket::SSL;
use Date::Parse;
        
my $output_file = '/home/joeblow/.conky/.gmail_unread';
my $max = $ARGV[0];

my $imap = Mail::IMAPClient->new
    ( User     => 'someguy@gmail.com',
      Password => 'supersecret',
      Socket   => IO::Socket::SSL->new
      (  Proto    => 'tcp',
         PeerAddr => 'imap.gmail.com',
         PeerPort => 993, # IMAP over SSL standard port
      ),
   );
$imap->select('Inbox');
my @unread = $imap->unseen or warn "Could not find unseen msgs: $@\n";

unless (scalar(@unread))
  {
  unlink $output_file;
  exit;
  }

my(@lines);
my $count = 0;
foreach my $msg_id (@unread)
  {
  $count++;
  if ($count > $max)
    {
    push(@lines,"More...\n");
    last;
    }
  my $date = convert_time($imap->get_header($msg_id, "Date"));
  my $from = $imap->get_header($msg_id, "From");
  my $subject = $imap->get_header($msg_id, "Subject");
  push(@lines, "$from - $date\n $subject\n");
  }
open(OUT,">$output_file");
print OUT (@lines);
close(OUT);

sub convert_time
  {
  my $old_time = str2time(shift);
  my $seconds = time() - $old_time;
  my $time_string;
  if (int($seconds / 3600))
    {
    $time_string .= (int($seconds / 3600).'h');
    $seconds = $seconds = int($seconds / 3600);
    }
  if (int($seconds / 60))
    {
    $time_string .= (int($seconds / 60).'m');
    $seconds = $seconds = int($seconds / 60);
    }
  if ($seconds)
    {
    $time_string .= ($seconds.'s');
    }
  return "$time_string ago";
  }

```

I set up crontab with a line like this(the 5 is a limit of 5 messages, newest first):
```
* * * * * /home/joeblow/.conky/gmail.pl 5
```

Then I need only have conky check if the output file is there then show it.

```
${if_empty ${exec cat ~/.conky/.gmail_unread}}${else}$stippled_hr
${alignc}You have unread gmail messages:

${exec cat ~/.conky/.gmail_unread}${endif}
```

---

### Post by StrixVarius on 2008-07-21
Alternative conky gmail script.

Hi guys. I took a gmail script written in Python by Baishampayan Ghose and modified it to work well with Conky. Some benefits to this:

1) Simplicity. No need to mess with cron and temp files
2) Efficiency. The script is only called when Conky needs it, and conky keeps the latest output in a buffer rather than refreshing it from a file every time conky updates its display.

Requirements:
- Python (apt-get)
- A newer version of conky (that supports $execpi)
- The urllib and feedparser Python libraries (apt-get)

I hope it's useful to you!

~/.conky/gmail_parser.py
```

## check-gmail.py -- A command line util to check GMail -*- Python -*-
## modified to display mailbox summary for conky

# ======================================================================
# Copyright (C) 2006 Baishampayan Ghose <b.ghose@ubuntu.com>
# Modified 2008 Hunter Loftis <hbloftis@uncc.edu>
# Time-stamp: Mon Jul 31, 2006 20:45+0530
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================

import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed
from textwrap import wrap

_URL = "https://mail.google.com/gmail/feed/atom"

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]

urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (uname, password)
	
def auth():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(_URL)
    feed = f.read()
    return feed

def readmail(feed, maxlen):
	'''Parse the Atom feed and print a summary'''
	atom = feedparser.parse(feed)
	print '${color}Mail: %s@gmail.com (%s new)\n' % (uname, len(atom.entries))
	for i in range(min(len(atom.entries), maxlen)):
		print ' ${color}"%s"' % atom.entries[i].title
		print '    ${color lightgrey}%s' % atom.entries[i].author
	if len(atom.entries) > maxlen:
		print ' ${color}more...'

if __name__ == "__main__":
    f = auth()  # Do auth and then get the feed
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser

```

~/.conkyrc
```

${execpi 300 python ~/.conky/gmail_parser.py username password numlines}

```

(example: ${execpi 300 python ~/.conky/gmail_parser.py user.name password 3})

Cheers!
H

---

