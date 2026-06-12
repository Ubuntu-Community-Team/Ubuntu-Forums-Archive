---
title: "Keyboard settings (latvian letters &#257; &#275; &#299; &#363; &#311; &#291; &#326;)"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Ji31 on 2007-04-29
Hi,
the changing of keyboard is running well, also the changing by the mouse is running (someone has finallly patched the bug??).

But, when I switch to latvian keyboard, it is not working. The keyboard settings are english and letters as
**&#257; &#275; &#299; &#363; &#311; &#291; &#326;** aren't there.

But switching between czech and english keyboard is ok. Do I need to install some language pack or something like that?

Thanks.

PS: my system is running in czech language and I use 6.10.

---

### Post by Ji31 on 2007-04-30
Really nobody knows?

Please, it's really important....do I need some specific fonts or something?

---

### Post by augrrr on 2008-04-02
Did you find an answer to getting those Latvian chars?  The solution would be of great interest to me too. In addition to the above letters, the o with the bar on top, the s with the v on top, the c with the v on top would be additional letters for the Latvian alphabet.

---

### Post by Perfect Storm on 2008-04-03
I don't know if this a help, but you can put "Character Palette" which can make these letters in your panel.

---

### Post by augrrr on 2008-04-08
Thanks.  That might be better than nothing at all.  If I can "define" the characters so that the ones I need are just "one click away", then that will be ok.  But ideally, it would be nice to define a 2-key macro for each character I need.

---

### Post by tty15 on 2008-07-13
Here's how I do it Debian. 

You'll place some files in /usr/local/bin or elsewhere in your path (and of course chmod a+x them). 

File #1 -- I give this the filename "latviski" 

this file has two lines
----------------------

file "latviski"'
---------------------

setxkbmap lv -variant apostrophe
xterm -geometry 25x5 -fn -*-Fixed-bold-r-*-*-*-180-*-*-iso8859-* -e msg_latv

--------------------------

ok, all you need is the first line, actually -- that's the ticket. You can also enter it on the command line manually, if you wish. 

You type the apostrophe key, and then the letter like this: &#257; &#353; &#269; 

that was 6 keystrokes not counting spaces.  

If you want an apostrophe, hit the apostrophe key twice. 

second file: called "angliski", which means "in english" in latvian. 

and the whole font thing:

"-*-Fixed-bold-r-*-*-*-180-*-*-iso8859-*--" 

just use the program "fontsel" -- play around with it a little bit, and you can choose your font -- that's just a font I chose I thought it looked good. The whole geometry thing and all can be tweaked as well. You can even drop the second line altogether (but it helps non-computer savvy people). 

----------------------------
file "angliski"
----------------------------

setxkbmap us
xterm -geometry 25x5 -fn -*-Fixed-bold-r-*-*-*-180-*-*-iso8859-* -e msg_angl

-------------------------------

this one gets you back to where you were. 

Now to explain the second lines 

--------------------------
file "msg_latv" 
---------------------------

echo
echo
echo "Tagad raksti Latviski"
sleep 5

-----------------------------

"Tagad raksti Latviski" means "now you are writing in latvian" in Latvian. It just pops up an xterm that tells you what's up.(actually the files "latviski" and "angliski" are popping up the xterm, these files just contain the stuff that the xterm prints out) This helps non-computer savvy Latvian folks realize what's going on. 

----------------------------
file "msg_angl
------------------------------

echo
echo
echo "Tagad raksti Angliski"
sleep 5
----------------------------------

I'll let you guess what "Tagad raksti Angliski" means. 

Both "msg_latv" and "msg_angl" are located in /usr/local/bin as well. (same directory as the files "latviski" and "angliski"). 


So... to tie this all together, you make icons (I have small icons of an American flag and a Latvian flag which execute the files "/usr/local/bin/angliski" and "/usr/local/bin/latviski", respectively. You could also add menu items, or just type the commands from the command line, depending on your window manager/desktop environment (I have this running on Gnome, but that's not really important). 

Doing it this way helps non-computer savvy Latvians because a little window pops up telling them what language (keyboard setting) they are writing in, stays there for 5 seconds (you can adjust this by changing the number after "sleep", and then goes away. 

For command line use, all you need to know is 


"setxkbmap lv -variant apostrophe"  

to get there

and

"setxkbmap us"

These commands have no text output. 

----

It took me a while, and this can probably be tweaked, and maybe you should type #!/bin/bash at the beginning of each of those files (I didn't, but technically, maybe one should).

There are other "variants", but the apostrophe variant is, in the opinion of most people, the best -- better than using the altgr key (right-hand alt key used to be green on old clicky-style keyboards) -- but it's supposed to actually mean "alternate graphics" -- or the tilde key way up left of the number one and shifted (yikes!). 

variant apostrophe is the way to go, man. It's so easy in Linux, yet a bit more complicated in XP (there's a hack to get the apostrophe variant, but hard to find on the internet). 

You could definitely tweak this, but this is the basic idea.


To make this easy: 

If you're not setting this up for someone else, just use the command

setxkbmap lv -variant apostrophe

just type that into your command line, then

setxkbmap us

to get back

or in the case of the OP, it might look like

setxkbmap cz (the get back to czech). 

there's also cz_qwerty, apparently, as well. 

The method using files and pop-ups is just how I would set up a computer with Linux for a relative who needs to use the Latvian language. 

all you really need are the setxkbmap commands, that's all. That's what really makes it work.

---

