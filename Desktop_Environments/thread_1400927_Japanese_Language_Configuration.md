---
title: "Japanese Language Configuration"
date: 2010-02-07
forum: Desktop Environments
---

### Post by nexist on 2010-02-07
Is there a step by step guide for setting up Japanese Language input for Gnome with Ubuntu 9.10? Maybe I am not searching correctly, but I am not finding it.

I have a US keyboard. I would like to type in the romanji and have it become Hiragana, Katakana and (hopefully) Kanji.

---

### Post by mushwars on 2010-02-07
install ibus then install anthy.

THen you will have a little keyboard icon next to your clock that you can click and choose anthy and you can input japanese. I have used it for years.

when you hit spacebar you will get a list of kanji options, make sure you recognize the kanji it is sometimes wrong.

---

### Post by nexist on 2010-02-07
> **mushwars said:**
> install ibus then install anthy.

THen you will have a little keyboard icon next to your clock that you can click and choose anthy and you can input japanese. I have used it for years.

when you hit spacebar you will get a list of kanji options, make sure you recognize the kanji it is sometimes wrong.

All I get is a "no input window message".

---

### Post by mushwars on 2010-02-07
I do to in firefox, its because it doesnt use Ibus input, go to a terminal right click and choose input method ibus, then click the little keyboard.

---

### Post by nexist on 2010-02-07
> **mushwars said:**
> I do to in firefox, its because it doesnt use Ibus input, go to a terminal right click and choose input method ibus, then click the little keyboard.

That did it. Is there no way to enable Japanese in Firefox/Open Office/etc as well? 

&#12354;&#12426;&#12364;&#12392;&#12372;&#12376;&#12414;&#12377;

---

### Post by mushwars on 2010-02-07
&#20309;&#12391;&#19990;&#12487;&#12473;&#12363;&#65311;
(nande yo desu ka?!)

[s]why were you able to get it to work in firefox and I CANT?![/s]
I see you have the same problem.


btw, if you hit space after each word instead of puting them all in a row it converts to kanji.

arigato gozaimasu becomes

&#26377;&#36032;&#12392;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#65281;&#65281;&#65281;


EDIT: I found what I need unfortunately it wont help you
[http://www.gentoo-wiki.info/Input_Methods](http://www.gentoo-wiki.info/Input_Methods)

---

### Post by nexist on 2010-02-07
> **mushwars said:**
> &#20309;&#12391;&#19990;&#12487;&#12473;&#12363;&#65311;
(nande yo desu ka?!)

[s]why were you able to get it to work in firefox and I CANT?![/s]
I see you have the same problem.


btw, if you hit space after each word instead of puting them all in a row it converts to kanji.

arigato gozaimasu becomes

&#26377;&#36032;&#12392;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#65281;&#65281;&#65281;


EDIT: I found what I need unfortunately it wont help you
[http://www.gentoo-wiki.info/Input_Methods](http://www.gentoo-wiki.info/Input_Methods)

Why can't we get SCIM to work? It is installed? Will it allow for typing in applications such as Firefox & OpenOffice?

---

### Post by mushwars on 2010-02-07
> **nexist said:**
> Why can't we get SCIM to work? It is installed? Will it allow for typing in applications such as Firefox & OpenOffice?
yes SCIM should work for you, I am saying that I can get ibus working for me because I can recompile packages to use ibus support where as you cannot. there have been several japanese input questions in the past few days do a search They will tell you how to use SCIM good luck.

---

### Post by mushwars on 2010-02-09
Sorry for bumping this thread, but You do not want ibus, it only can input into programs that support ibus, instead install uim ( if it doesnt already come installed ) then right click on your menubar and add the uim gtk. 

You might need to do this

~/.xinitrc
```
export XMODIFIERS=@im=uim
export GTK_IM_MODULE=uim
export QT_IM_MODULE=uim

```

---

### Post by Zorael on 2010-02-11
SCIM, ibus and UIM should all work. The sole exceptions I know of at this time are Kate and KWrite 4.4, which only work with UIM (via its XIM wrapper).

If OpenOffice.org doesn't work, see if it works in **xterm**. If it doesn't, you probably need to correct a variable in a certain file.

---

### Post by Zorael on 2010-02-11
I threw together a script that does a bunch of checks and saves a log of the results in your home directory (**~/input-method-info.log**). With the output from there it should be easy to see what still needs to be done if your input method of choice (ibus, UIM, Scim, etc) isn't working for you.

Set it as executable and run it from a terminal - that way you can see any error output it spews out. Attach the produced log to a reply here.

**If your terminal language isn't English**, the script needs to be edited to correct three strings. The correct strings can be found in the top part of the output of '**im-switch -l**'.
```
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/zorael/.xinput.d/en_US" is defined as a link pointing to
ibus
[COLOR="RoyalBlue"]**This private configuration _supersedes_ the system wide default.**[/COLOR]
=======================================================
[COLOR="RoyalBlue"]**_The system_ wide default is pointed by** [/COLOR]"/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
[COLOR="RoyalBlue"]** _link currently_ points to**[/COLOR] ibus
```

In the section at the top of the script, there are three variables that must contain something unique to those *lines* highlit in blue above. Not necessarily the strings I chose ("supersedes, "The system" and "link currently") - just something unique to them.
```
# localization; change these terms if terminal language isn't English
# refer to the output of im-switch -l for the correct translations
SUPERSEDES=[COLOR="RoyalBlue"]**"supersedes"**[/COLOR]
THESYSTEM=[COLOR="RoyalBlue"]**"The system"**[/COLOR]
LINKCURRENTLY=[COLOR="RoyalBlue"]**"link currently"**[/COLOR]
```
Use any text editor to make your changes.

---

