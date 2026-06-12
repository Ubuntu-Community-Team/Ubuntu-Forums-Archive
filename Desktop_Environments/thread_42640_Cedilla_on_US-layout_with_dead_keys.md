---
title: "Cedilla on US-layout with dead keys"
date: 2005-06-18
forum: Desktop Environments
---

### Post by Zunino on 2005-06-18
Hello.

I have tried to search around for a solution to this nagging issue with the cedilla character (ç) on systems with a US-layout keyboard. On every other system I have seen and used, that character is input by hitting the apostrophe key <'> and then the letter <c>. That's not only customary, but it is way less cumbersome than the composing solution on Kubuntu, which involves pressing <right ALT> + <,> and then <c>.

Is there a way to fine tune my desktop so that pressing <'> and then <c> gives me a cedilla as opposed to the funky accented c? I read somewhere that that was the expected result on a Unicode-enabled Linux system, but I'd rather give up Unicode than put up with this annoyance. I also tried fiddling around with a keyboard mapping file (I can't remember which), changing the composition result of pressing <'> and <c> and commenting out the rules for making up the accented c, but it did not work, even after restarting.

Any help would be greatly appreciated.

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by easy_target on 2005-07-24
I have the same problem as Zunino. Being a portuguese speaker, when it comes to typing large texts (I do translation of technical texts) composing can be VERY annnoying. I tried the same thing on Xandros and it worked fine (no composing, which means no need to press compose key+ , + c). Is there a workaround for this?

Thanks in advance.

---

### Post by easy_target on 2005-07-31
[QUOTE=easy_target]I have the same problem as Zunino. Being a portuguese speaker, when it comes to typing large texts (I do translation of technical texts) composing can be VERY annnoying. I tried the same thing on Xandros and it worked fine (no composing, which means no need to press compose key+ , + c). Is there a workaround for this?

Thanks in advance.[/QUOTE]
 bump?

---

### Post by vdorta on 2005-07-31
I need to write in Spanish and French, so I switched from Ubuntu to Kubuntu mainly because the keyboard settings in KDE, unlike Gnome, are at least global, but the final solution should be a "us_intl with deadkeys" layout that neither one offers. I tried to change settings in the Ubuntu xorg.conf file and made a big mess.

---

### Post by easy_target on 2005-08-01
That is very unfortunate. A friend of mine has Xandros installed and the accents work flawlessly. Is there a patch for that?

---

### Post by melissawm on 2005-12-10
I've posted several times in this topic already (in other threads) but since nobody seems to offer a definitive solution... here i am again ;) Same problem.. any ideas?

---

### Post by ffurlanete on 2005-12-21
I've changed the file /etc/environment in the line: LANG=pt_BR.UTF-8 to LANG=pt_BR and it worked.

Oh no. Forget it. It brokes cedilla in OO.org.

---

### Post by ffurlanete on 2005-12-21
Ok, I think I got it!

Type 'sudo dpkg-reconfigure locales'

then generate new locale: pt_BR ISO-8859-1
then select default locale: pt_BR ISO-8859-1

reinit your kde session.
that's it.

---

### Post by ubuntumaneh on 2005-12-21
I dont think this deserves a new thread, for the problem is similar. I wished to have cedilla on a terminal (xterm) or some way I can type cedilla in nano (or pine). Now, even after applying you solution I could't get it. In my desktop computer a solved it, just having a proper keyboard, but for the laptop this would be a nuisance. Does someone know how to solve this?

BTW, this is not an issue in emacs, gladly!!

---

### Post by ffurlanete on 2005-12-21
I did use the same solution in my laptop (a toshiba satellite) and it worked...

---

### Post by ubuntumaneh on 2005-12-21
I did't follow you. Sorry. BTW, I have a satellite myself. Anyway, I used your solution, and I can get any cedilla or accented character in xterm. Im confident that in OO I can have, but I don't need this app. So, what do you mean by "the same solution worked"? Maybe I have to do something else to get the cedilla in xterm.

---

### Post by ffurlanete on 2005-12-22
I'm reading again your previous post and i think that I hadn't understood it. I apologize.  

I did mean that I had the same problem on both machines: I had cedilla working on all applications except the Qt/KDE ones. 
Your problem seems to be in the xorg.conf file. Maybe a 'sudo -plow dpkg-reconfigure xserver-xorg' should work or else you could send me a copy of the section of your xorg.conf that configures the keyboard. Mine is:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
EndSection

---

### Post by ubuntumaneh on 2005-12-22
Solved the problem. Thanks a lot.
The driver was "keyboard" and not kbd.

---

### Post by ffurlanete on 2005-12-22
You're wellcome.

---

### Post by UphillSkier on 2005-12-24
Are your dead keys working ok?  ( I mean typing ' then e to get é?

If not, check out this post [http://ubuntuforums.org/showpost.php?p=465307&postcount=13](http://ubuntuforums.org/showpost.php?p=465307&postcount=13)

Once the dead keys are working, try pressing the right Alt key and the comma key 
at the same time: çççççççççççç !

good luck
Andy

---

### Post by ispmarin on 2006-02-08
Alt+`+c for cedilla is extremely inconvenient. What we have to do to get the old and good `+c?

---

### Post by codas on 2006-09-14
Dear All!

Is is possible to  use ' + c in order to get cedilla (cedilha) in Ubuntu?


Thanks!

Best regards,
Daniel

---

### Post by ispmarin on 2006-09-14
Yes, it is possible, at least for Dapper Drake. Choose the locale as pt.BR-UTF-8, and chooses the international keyboard. Works for me.

---

### Post by codas on 2006-09-14
Thanks!  But please, may you be more specific?

What is Dapper Drake?

How may I choose the locale as pt.BR-UTF-8?

Thanks a lot!

Best regards,
Daniel

> **ispmarin said:**
> Yes, it is possible, at least for Dapper Drake. Choose the locale as pt.BR-UTF-8, and chooses the international keyboard. Works for me.

---

### Post by codas on 2006-09-14
Great!

Here is my new /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="pt_BR.UTF-8"
# en_US.UTF-8"
# LANG="pt_BR"
LANGUAGE="en_US:en_GB:en"




> **ispmarin said:**
> Yes, it is possible, at least for Dapper Drake. Choose the locale as pt.BR-UTF-8, and chooses the international keyboard. Works for me.

---

### Post by livia on 2007-01-31
It worked for me too! =] Thank you! 
Valeu!

---

### Post by pensador82 on 2007-02-11
I also having this problem. I am Brazilian naturilized Canadian, so I have "English (Canada)" as my default language, but I use "U.S. English International (with dead keys)" for the accents.

On Windows, I would use the equivalent setup and when I press [COLOR="DarkGreen"]'[/COLOR] and [COLOR="DarkGreen"]c[/COLOR], I would get [COLOR="DarkGreen"]ç[/COLOR]. How can I make that happen on Ubuntu?

I tried
[FONT="Courier New"][COLOR="DarkGreen"] sudo gedit /etc/environment[/COLOR][/FONT]
and
[FONT="Courier New"][COLOR="DarkGreen"] sudo dpkg-reconfigure locale[/COLOR][/FONT]
but nothing. Please help!

---

### Post by revertex on 2007-04-28
Surelly it's the most annoying bug ever.

It seems impossible to mix LC variables in ubuntu.

All that i want is use everithing in english but accents in portuguese, like ' + c to get cedilla.

Sounds simple, but seems like nobody can get it to work.

In my old gentoo install all that i need was set LC_CTYPE=pt_BR.ISO-8859-1 and cedilla works as intended.

In ubuntu it almost drive me crazy, i can't find any doc that point me how to change it.

---

### Post by ispmarin on 2007-04-28
I was hoping that this matter was over centuries ago... it seems not. I am using now pt_BR-UTF-8, and all the accents works right, but did not install all the language packs, so some parts of my system are on english. I will try as soon i hit home to change the language and sees if english with keyboard as english with dead keys will work.

---

### Post by pensador82 on 2007-04-28
I found a way to get around that problem. Have a look at this short article:
[http://pensador.org/blog/107/Tutorials/How-to-get-a-c-cedilla-on-Ubuntu.php](http://pensador.org/blog/107/Tutorials/How-to-get-a-c-cedilla-on-Ubuntu.php)

---

### Post by revertex on 2007-04-28
> **pensador82 said:**
> I found a way to get around that problem. Have a look at this short article:
[http://pensador.org/blog/107/Tutorials/How-to-get-a-c-cedilla-on-Ubuntu/](http://pensador.org/blog/107/Tutorials/How-to-get-a-c-cedilla-on-Ubuntu/)

Thank you anyway, but it's more a work around than a solution.

This only works with Gnome and other DE, not with  WM like Openbox or FVWM.

And what about you want to use everything  in english with us keyboard but write in portuguese?

I want compose cedilla the simple way, just ' plus c.

It's pretty simple to achieve with gentoo, the distro that i used to use, all that i need is edit /etc/env.d/02locale this way.

```
LC_CTYPE=pt_BR.ISO-8859-1
LC_NUMERIC=pt_BR.ISO-8859-1
LC_TIME=pt_BR.ISO-8859-1
LC_COLLATE=pt_BR.ISO-8859-1
LC_MONETARY=pt_BR.ISO-8859-1
#LC_MESSAGES=pt_BR.ISO-8859-1
LC_MESSAGES=en_US.ISO-8859-1
LC_PAPER=pt_BR.ISO-8859-1
LC_NAME=pt_BR.ISO-8859-1
LC_ADDRESS=pt_BR.ISO-8859-1
LC_TELEPHONE=pt_BR.ISO-8859-1
LC_MEASUREMENT=pt_BR.ISO-8859-1
LC_IDENTIFICATION=pt_BR.ISO-8859-1
```

LC_MESSAGES is intencionally commented because i want console messages in english.

I guess the ubuntu 02locale counterpart is /etc/enviroment, but edit this file was no results.

Even worse, before play with some files in a desesperated attempt to fix it, now my system is POSIX, and i dunno how to get it back in en-us-utf8.

I really like ubuntu package manager, the multitude of packages avaliable, the strongness, but the lack of control and flexibility is a weak point that need to bi fixed.

If you change anything that comes by default you get a broken system.

Looks like except the people involved in this thread all other people in my country are happy windows users (running cheap pirated copy for sure).

---

### Post by ispmarin on 2007-04-30
Right now, using keyboard as us:intl with dead keys, and locale as pt_BR-UTF8, everything works right. Dunno with en_us-UTF8, but i think that as long you system is UTF8 and your keyboard is us:intl with dead keys, everything should work...

---

### Post by Marchash on 2008-02-01
Changing your locale (LANG=whatever) may work but it is a major change that can have an impact on many other things in your system, possibly not wanted.

If you want to fix ONLY this problem, there is a much narrower solution.

Log in as root, make a backup copy of this file:
  /usr/share/X11/locale/en_US.UTF-8/Compose
then search and replace "&#263;" by "ç" and  "&#262;" by "Ç".

Restart your applications so they can take the change into account.

Warning: many applications implement this "fix" by themselves,
whatever X11 configuration is. To test that you really changed X11
configuration you have to use a "dumb" application like xterm or xev.

en_US.UTF-8/Compose is included by most locales, so editing changes
the behaviour for most languages. It might be possible to restrict the
change to one locale but I did not succeed.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296599](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296599)

---

### Post by brenoelvio on 2008-04-29
What I did was:

System -> Administration -> Language Suport

Choose Portugues and them after installing choose Português Brazil.
Them after restarting the system, go to:

Sistema -> Preferencias -> Teclado

Choose Layout: EUA -> Internacional Alternativo (antigo us_intl)

This solution is for Brazilians and Portuguese :P

The only bad thing is that the Ubuntu System goes portuguese. But the keyboard works perfectly.

You can always goe back if you dont get use to your native language :P

---

### Post by darksoul7 on 2008-07-15
> **Marchash said:**
> Changing your locale (LANG=whatever) may work but it is a major change that can have an impact on many other things in your system, possibly not wanted.

If you want to fix ONLY this problem, there is a much narrower solution.

Log in as root, make a backup copy of this file:
  /usr/share/X11/locale/en_US.UTF-8/Compose
then search and replace "&#263;" by "ç" and  "&#262;" by "Ç".

Restart your applications so they can take the change into account.

Warning: many applications implement this "fix" by themselves,
whatever X11 configuration is. To test that you really changed X11
configuration you have to use a "dumb" application like xterm or xev.

en_US.UTF-8/Compose is included by most locales, so editing changes
the behaviour for most languages. It might be possible to restrict the
change to one locale but I did not succeed.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296599](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296599)

I tried that and no luck. I just can't get used to typing Alt + , for ç. I REALLY need my ' + c back. 

It just takes me way too long to type in French and that bugs me. Since I live in Western Canada, I mostly communicate in English so I need the English setup, but when I chat with family back in Québec, I need to type in French. Anyway, I know this is the dog that won't die, but I would really love a solution. 

Cheers!

---

