---
title: "Does anybody love their gmail setup?"
date: 2010-03-03
forum: Desktop Environments
---

### Post by sameat on 2010-03-03
I'm looking for the best way to use gmail in 9.10,

Currently I use it this way:

I run cairo-dock (no panels)
I have a prism app for gmail

I feel that I am missing the following:
-Any kind of a notification system...I would prefer something in the dock.
-Optimizations/extensions in firefox...haven't seen how to apply them to prism.


What is everybody's favorite way of achieving an integrated gmail solution?

Thanks

---

### Post by sameat on 2010-03-03
I saw this thread:

[http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+prism](http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+prism)

but I'm still up for other suggestions.

---

### Post by alindgr1 on 2010-03-03
I have mine setup in Opera, and I like it that way.  There is a notification that it pops up in the bottom right corner, and the icon on the side bar gets a little red dot on it.  Opera handles email through both POP3 and IMAP, also.  I have mine set up through IMAP, I don't have to get into Gmail on the website also.

The only problem I have with opera is embedded Flash videos. I am working on it though, hopefully I'll have it fixed soon.

---

### Post by fabounet on 2010-03-04
there is a mail applet in Cairo-Dock, it supports multi-accounts and Gmail quite well.

---

### Post by genux05 on 2010-03-04
is there one for kubuntu as well ? because I have my gmail opened in a tab in FF and just check every once and a while.  because if you edit your gmail emails the google toolbar also updates with the mail icon.. which I just find kinder annoying and turned off.

---

### Post by stinkeye on 2010-03-04
I use conky to check gmail and display a popup in the notification  area and play a sound file.
Can post how to and files if your interested.

---

### Post by sameat on 2010-03-04
fabounet is absolutely correct...I had somehow missed the mail-applet and that suits me just fine.  I switched from prism to chrome for gmail, and extensions are available again.

Cairo-dock is a great tool and rock solid on my system.  The configuration screens can be a bit overwhelming, but that might just be the price of customizabililty.

---

### Post by solitaire on 2010-03-04
> **stinkeye said:**
> I use conky to check gmail and display a popup in the notification  area and play a sound file.
Can post how to and files if your interested.

Oh can you post a HowTo for that!
I'd love to set that up for my Conky...

---

### Post by stinkeye on 2010-03-04
> **solitaire said:**
> Oh can you post a HowTo for that!
I'd love to set that up for my Conky...

Firstly, if you don't want to change any of the paths save everything in 
your home directory in a folder named conky .
To display the image you need the conky-all package in synaptic.
You can copy and paste these scripts or use the ones in the attachment.
The attachment also includes a wav file and icon.

Save as conkygmail
```
background yes
update_interval 3.0
total_run_times 0

own_window yes

own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
minimum_size 500 150   
maximum_width 500 
alignment tr

gap_x 15
gap_y 830

use_xft yes
xftfont Sans:size=8
xftalpha 1.0
uppercase no
override_utf8_locale yes
use_spacer right


default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00

draw_shades no
draw_outline no
draw_borders no



cpu_avg_samples 2
net_avg_samples 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

draw_graph_borders yes
stippled_borders 0

short_units yes
pad_percents 0
# set to yes if you want all text to be in uppercase
uppercase no

max_specials 1024
max_user_text 4000
text_buffer_size 2048

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49



TEXT
${if_match "${execi 900 perl ~/conky/gmail.pl n}" >= "1"}${image ~/conky/gmail2.png -s 48x48 -p 0,0}
${color AD00FF}${font Sans:size=10}${goto 70}${voffset 15}${execi 900 perl ~/conky/gmail.pl n} Unread${font}${color}

${execi 900 ~/conky/newmail}${execi 900 perl ~/conky/gmail.pl s}${else}${endif}
```


Save as gmail.pl
```
#!/usr/bin/perl

# WARNING: Change name and password if posting!!

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="[COLOR="Red"]xxxxx[/COLOR]"; #username for gmail account
$pass="[COLOR="#ff0000"]xxxxx[/COLOR]"; #password for gmail account
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
[COLOR="#ff0000"]Insert username and password where highlighted[/COLOR]


Save as startconky (delays start until desktop loaded)
```
#!/bin/sh
# click to start, click to stop
 
if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 
sleep 30  # sleep not required for xfce on startup - 30 or more for others
conky -c ~/conky/conkygmail &
 
 exit
fi
```



Save as newmail
```
#!/bin/bash

notify-send -i ~/conky/gmail2.png "Gmail" "You have new mail" &
play -q ~/conky/message.wav
```



Make gmail.pl, newmail and startconky executable. 
(Right click > properties > permissions )


**[COLOR="#ff0000"]NOTES:[/COLOR]**
For notify-send to work you may need to install *libnotify1*
For the play command to work install *sox*
To autostart add the path to startconky to Startup Applications using the browse button.

To test in terminal```
conky -c ~/conky/conkygmail
```
[COLOR="DarkRed"]EDIT:[/COLOR]IF YOU HAVE NO UNREAD GMAIL YOU WON'T SEE ANYTHING

I don't think I've forgotten anything.
Any problems let me know.

---

### Post by Ms_Angel_D on 2010-03-04
Just a bit of FYI there is also googsystray [http://sourceforge.net/projects/googsystray/files/](http://sourceforge.net/projects/googsystray/files/) It works for gmail, google calendar, reader, wave, & voice. There is a .deb at the above link.

---

### Post by solitaire on 2010-03-04
Thanks!
it looks like it's working...

Just need to figure out how to pick up "Google Apps" Mail Account as well :D lol

---

### Post by stinkeye on 2010-03-04
> **solitaire said:**
> Thanks!
it looks like it's working...

Just need to figure out how to pick up "Google Apps" Mail Account as well :D lol
No problem.
Just a note, you will keep getting the messages until you check your gmail
account.If there is no new mail you won't see anything.
You can change the update interval by changing the three *execi 900* commands in the conkygmail config.
900=900 seconds.
By the way the wav file is from Monty Python and the Holy Grail.

---

### Post by maddg3241 on 2010-03-04
i use hotmail which works great you should try it instead

---

### Post by Diskbox on 2011-01-05
> **stinkeye said:**
> I use conky to check gmail and display a popup in the notification  area and play a sound file.
Can post how to and files if your interested.

ok this is by far the best gmail conky setup I've seen to date which is why I'm replying to an old thread, sorry.

I've been battling with this for hours now and still can't get it working.  Here's my console output:

```
Conky: desktop window (180004c) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x5e00001)
Conky: drawing to double buffer
--2011-01-06 00:46:53--  https://my.user.name:*password*@mail.google.com/mail/feed/atom
Resolving mail.google.com... 173.194.37.83
Connecting to mail.google.com|173.194.37.83|:443... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to mail.google.com:443.
HTTP request sent, awaiting response... 401 Unauthorized
Authorisation failed.

```

Note my username has two dots in it.  I've changed my password as that had special chars in it but that's not helped either.  Have also tried full email address as the username but to no avail.

The only thing I can see as to why it's breaking is the username is in the format [email]first.middle.last@gmail.com[/email] and not [email]first.last@gmail.com[/email]

If someone has anymore suggestions I'd love to try and get this working.

Cheers,
Diskbox

---

### Post by stinkeye on 2011-01-06
Try the rss feed in your browser to see if it works with...
```
https://[COLOR="Magenta"]username[/COLOR]:[COLOR="#ff00ff"]password[/COLOR]@mail.google.com/mail/feed/atom
```

or

Try to log in manually by going to
[https://mail.google.com/mail/feed/atom]("https://mail.google.com/mail/feed/atom")


May be a gmail account setting.
I use pop while imap is disabled.
Don't know if that matters.

There is also **gm-notify** in the repositories which integrates 
with the messaging menu.
Shows a notification bubble and new mail sound.

---

### Post by Diskbox on 2011-01-06
Hi stinkeye, thanks for coming back to me so quick.

This is odd.  I can hit the url in a browser and it works ok I can see the rss feed.

I've even tried on another machine and tried substituting the "."'s in my username for %2E, still no joy.

Don't suppose there's anything else I can try to get it working?

Cheers,
Diskbox

ps  I'd seen gm-notify but to be honest this script looks so much better.


**EDIT**
ok I'm getting somewhere.  I've just tried the python script from here: [http://tycho.ws/blog/2010/08/gmail-auth](http://tycho.ws/blog/2010/08/gmail-auth) and can get it to authenticate and pull my details ok.  Looks like there's something with your script that my account doesn't like :(

**EDIT 2**
Right.  If I run wget -O - https://$user:$pass@mail.google.com/mail/feed/atom --no-check-certificate and change $user and $pass for my details, substituting any special chars for the escape codes e.g %7B instead of { in the password then this also dumps out my emails.

Question now is, am I getting any closer or just going around in circles!?

---

### Post by stinkeye on 2011-01-06
Must be the script then????
I'll post it again for you to copy and paste.
```
#!/usr/bin/perl

# WARNING: Change name and password if posting!!

use Switch;
use Text::Wrap;

my $what=$ARGV[0];

$user="[COLOR="Magenta"]USERNAME[/COLOR]"; #username for gmail account
$pass="[COLOR="#ff00ff"]PASSWORD[/COLOR]"; #password for gmail account
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
Make sure it's executable and include quotations around password and username.

I don't know a lot abut scripting but it appears the last part of the script deals with 
escaping special characters in the password but not the username.
Possibly try putting a back slash before the dots in your username.

---

### Post by as2000 on 2011-01-06
I just use Thunderbird. :lolflag:

---

### Post by stinkeye on 2011-01-06
> **EDIT 2**
Right. If I run wget -O - https://$user:$pass@mail.google.com/mail/feed/atom --no-check-certificate and change $user and $pass for my details, substituting any special chars for the escape codes e.g %7B instead of { in the password then this also dumps out my emails.

Yeah I think your on the right track and you just need someone who knows how to insert your username in the right format.

---

### Post by Diskbox on 2011-01-06
Thanks!

I checked it with another account which didn't have periods in it's username and it works like a treat.

I'll play around with it some more tonight and see if I can work out how to add the username properly including dots.

Cheers,
Diskbox

---

### Post by stinkeye on 2011-01-06
Ok, good luck.


**[COLOR="Red"]EDIT:[/COLOR]**
I think this is the origin of the script.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=680265[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=680265")
See post #49 on page 5.

---

