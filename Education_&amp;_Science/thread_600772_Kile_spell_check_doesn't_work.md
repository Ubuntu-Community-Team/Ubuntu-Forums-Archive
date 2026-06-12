---
title: "Kile spell check doesn't work"
date: 2007-11-02
forum: Education &amp; Science
---

### Post by Lurkos on 2007-11-02
I've just installed Ubuntu 7.10 Gutsy Gibbon.
I've also installed kile and texlive-full.
The problem is that I can't use the spell checker into Kile: when I click on Tools->Spelling appears this message "The spelling program could not be started. Please make sure you have set the correct spelling program and that it is properly configured and in your PATH".
aspell and aspell-LANG are correctly installed, but I can't find where I can set the spelling program into Kile.
Can you help me?
It is very important, because I have to write my thesis.
Thanks!

---

### Post by earlycj5 on 2007-11-05
Presumably you need to use KDE's control center to set the spell checker to Aspell since Kile is a KDE app.

KDE Components -> Spell Checker

Maybe that'll help?

---

### Post by Lurkos on 2007-11-07
Thanks!
Now it works perfectly! :-D
However I can't understand why in Debian it works well directly without this procedure...

---

### Post by thecaptainzap on 2007-11-12
I'm having the same problem. I installed Kile, installed Apsell, and installed Kcontrol. I went into Kcontrol and made the required changes to the Spell Check settings, but nothing happened in Kile. When I try to run Spell Check it give me the same error. I went into the Kile settings and tried to change the dictionary, but I'm not sure where the aspell dictionary file is, in order to direct Kile to it, not to mention I don't even know if that is the problem.

Thanks for your help!
Tim

---

### Post by edantes on 2008-02-03
I will take the liberty of reviving this topic with a follow up question.

What about encoding?  Kile does not pass encoding information  to *aspell*.  

For instance. From the command line I can check files with non-default encodings:

```
aspell --encoding=iso-8859-1 -lpt_BR  check test.tex
```

With *kile*, only documents encoded with UTF8 can checked.  Otherwise, words with non-ASCII character will all be tagged  as misspelled.
 
Changing the defauts for the Spellcheker with KDE  *kcontrol* doesn't have any effect.  Is this fixable from inside Kile?

---

### Post by castudil on 2008-03-12
Thanks it worked! 
Just for future reference. this steps were what I followed:

1. open the Synaptic manager and install 
Kile
apsell
kcontrol

2. goto Applications->Other->Spell Checker

in client choose Aspell, this will change the dictionary to Aspell (for me by default appeared Ispell as dictionary).

3. restart Kile (if it is open)

---

### Post by buntu_hugenewbie11 on 2008-11-10
So I followed these directions and I still get the PATH error that people above did.
What do I need to do to make Kile spellcheck??

---

### Post by kinalus on 2008-12-05
Hi,

I had the same problem on Intrepid 8.10 with KDE4, I couldn't get it to work by following this thread, but by using a Hardy installation I found out what needs to be done.

The speller to use is stored the file:

```
~/.kde/share/config/kdeglobals
```

please _backup_ this file before proceeding.
Open the file in your text editor of choice and locate the section beggining with the line:
```
[KSpell]
```

The first line after that should be
```
KSpell_Client=0
```
as far as I understand this means "use ISpell", so simply by setting
```
KSpell_Client=1
```
and restarting kile, the program (and the rest of KDE) should now use ASpell.

Cheers, hope I helped.

Disclaimer, I know close to nothing about KDE's configuration files so please don't hate me if this breaks your configuration.

---

### Post by rustamych on 2008-12-20
> **kinalus said:**
> Hi,

I had the same problem on Intrepid 8.10 with KDE4, I couldn't get it to work by following this thread, but by using a Hardy installation I found out what needs to be done.

The speller to use is stored the file:

```
~/.kde/share/config/kdeglobals
```

please _backup_ this file before proceeding.
Open the file in your text editor of choice and locate the section beggining with the line:
```
[KSpell]
```

The first line after that should be
```
KSpell_Client=0
```
as far as I understand this means "use ISpell", so simply by setting
```
KSpell_Client=1
```
and restarting kile, the program (and the rest of KDE) should now use ASpell.

Cheers, hope I helped.

Disclaimer, I know close to nothing about KDE's configuration files so please don't hate me if this breaks your configuration.

I have no [KSpell] in this my file. When I put info as you suggested nothing happence. May be there is another solution?

---

### Post by centurian on 2008-12-31
Hi rustamych,

Try to add the following section
```

[KSpell]
KSpell_Client=1
KSpell_DictFromList=1
KSpell_Dictionary=american
KSpell_Encoding=0
KSpell_NoRootAffix=0
KSpell_RunTogether=0

```
If it still doesn't work, then try to install kate.

```
sudo aptitude install kate
```

Hopefully it would work

> **rustamych said:**
> I have no [KSpell] in this my file. When I put info as you suggested nothing happence. May be there is another solution?

---

### Post by dfmalh on 2009-02-04
Hi, how do I get the spell check to work in Kile on Ubuntu/Gnome?

Thanks.

---

### Post by oly_mistry on 2009-02-07
You just need to install ispell as suggested in 
[http://ubuntuforums.org/showthread.php?t=351492](http://ubuntuforums.org/showthread.php?t=351492)

---

### Post by dfmalh on 2009-02-11
Thanks, oly_mistry.

I installed "kate", did nothing. "aspell" was already installed. After I installed "ispell" (the last post ;-) on other post) it works great!

Thanks for the help.
:guitar:

---

### Post by Cenna on 2009-03-21
This is little radical approach but if you install "kubuntu-desktop" from package manager and restart kile it will fix the problem. Maybe installation of kate and aspell is also enough.

It adds only 360 MB to the system which is not really big deal with todays hard disks. You can enjoy KDE sometimes too.

---

### Post by Krzysztof on 2009-04-28
> **centurian said:**
> Hi rustamych,

Try to add the following section
```

[KSpell]
KSpell_Client=1
KSpell_DictFromList=1
KSpell_Dictionary=american
KSpell_Encoding=0
KSpell_NoRootAffix=0
KSpell_RunTogether=0

```


This worked perfectly for me. 
Thank you!

K.

---

### Post by ceciliaFX on 2009-06-15
> **Krzysztof said:**
> This worked perfectly for me. 
Thank you!

K.
I already seemed to have Aspell installed on my 8.10 OS but was having trouble getting Quanta plus to spell check.

it took a while to find that info but I added those lines to the ~/.kde/share/config/kdeglobals file and BOOM!

after starting up Quanta it works! just like that!

thank YOU!

---

### Post by norman_h on 2009-08-10
> **oly_mistry said:**
> you just need to install ispell as suggested in 
[http://ubuntuforums.org/showthread.php?t=351492](http://ubuntuforums.org/showthread.php?t=351492)

+1

---

### Post by mr_ioso on 2009-09-21
Hi,

I solved the problem!! Unfortunately not for Kile but for lateX under linux in general.
Another editor, called texmaker, integrates the open-office spellchecker and works as
good as kile does.

[http://www.xm1math.net/texmaker/download.html](http://www.xm1math.net/texmaker/download.html)

I hope this helps.

-- mr.ioso

---

### Post by myle on 2009-09-22
[http://bugs.kde.org/show_bug.cgi?id=33857](http://bugs.kde.org/show_bug.cgi?id=33857)

---

### Post by Benj_C on 2010-01-20
Hi,

I'm running Kile 2.1 Beta 2 on my latptop with Ubuntu Karmic. This version of Kile uses KDE 4.3.2. I installed Ispell and Kate (not really sure why somebody recommended Kate though...). I also installed qt4-config and try some other stuff, but never saw any section about spell-checking in there.

1. The spell checker seems to work, but it is completely retarded. It checks every single LaTeX command (Come - on!!). In other word, it is useless. I won't spend 5 minutes ignoring every single word in my preamble before being able to check my document.
I'm pretty sure this was already doing the same thing before Ispell. So I don't know if it recognized by Kile.

2. I can't have the Spell-Check as I type. In Kile, if I go to Tools, I cannot click on "Spellcheck Selection".

Could anybody help me? Would be much appreciated as I use LaTeX daily!

Best,

Ben

---

### Post by seul on 2010-02-25
ispell +1

---

### Post by mrkeef on 2010-03-03
> **centurian said:**
> Hi rustamych,

Try to add the following section
```

[KSpell]
KSpell_Client=1
KSpell_DictFromList=1
KSpell_Dictionary=american
KSpell_Encoding=0
KSpell_NoRootAffix=0
KSpell_RunTogether=0

```
If it still doesn't work, then try to install kate.

```
sudo aptitude install kate
```

Hopefully it would work

That worked fine for me (9.10) I haven't installed KDE but use kdissert a bit and was frustrated by lack of spell checking

---

### Post by zebraneo on 2010-10-01
that was helpful but you have to tell people where to put the code what file, I didn't know and I had to find out and now it works thank you

---

### Post by seul on 2010-10-02
> **zebraneo said:**
> I didn't know and I had to find out and now it works thank you

Maybe it will help others if you share the details.

---

### Post by ItalOz on 2011-03-03
in the latest version of Kile 2.0.85
running under Ubuntu 10.04 (gnome) the spell checker of was running out of the box, but only english US

for installing another language there is no need to install the kcontrol that is not anymore in synaptic but you only need to go in synaptic type [FONT="Courier New"]aspell[/FONT] in the search window and install what suits your language

There is nothing inside Kile to install a new dictionary, I spent hours in there... ](*,)

Hope it helps

---

