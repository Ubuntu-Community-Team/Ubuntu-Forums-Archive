---
title: "Why isn't Filezilla readily available in Ubuntu 9.04?"
date: 2009-05-23
forum: General Help
---

### Post by kbdunn on 2009-05-23
I was able to install it with no problem in 8.10.  Now when I try to add it via Add/Remove I get this error:

[COLOR="Red"]FileZilla FTP client cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.[/COLOR]

---

### Post by mellowd on 2009-05-23
tried it via the command line yet?

---

### Post by Kareeser on 2009-05-23
You might be trying to install the 32-bit version on 64-bit. Try **mellowd**'s suggestion:

```
sudo apt-get install filezilla
```

---

### Post by growled on 2009-05-23
Yeah, try installing with the command line and post any error messages. It installs perfectly for most of us.

---

### Post by kbdunn on 2009-05-24
Command line install did it.  Thanks a lot, everyone!  I'm running 32 bit, by the way, and I didn't have to use the command line to install on 8.10.  What can I say?  I can be lazy sometimes. ;)

---

### Post by oldos2er on 2009-05-24
"[COLOR=Red]FileZilla FTP client cannot be installed on your computer type (i386)" [COLOR=Black]would indicate you're running 64-bit Ubuntu.[/COLOR]
[/COLOR]

---

### Post by moeshroom on 2009-05-29
> **oldos2er said:**
> "[COLOR=Red]FileZilla FTP client cannot be installed on your computer type (i386)" [COLOR=Black]would indicate you're running 64-bit Ubuntu.[/COLOR]
[/COLOR]

In my case I am running 64 bit Ubuntu and it returned:
[COLOR=Red]"FileZilla FTP client cannot be installed on your computer type (amd64)"[/color]

The command line installation worked though :)

---

### Post by openmn on 2009-05-31
I am running 32-bit Jaunty and it wouldn't let me install through add/remove [FileZilla FTP client cannot be installed on your computer type (i386)]. Command line worked fine though. I would assume there is a glitch somewhere that caused this.

---

### Post by lake54 on 2009-06-03
Yeah just to add to this, I added the package via Synaptic - worked perfectly. Don't know why it did so in the Application thing. Running 32-bit 9.04 after upgrade from 8.10 (which incidentally the upgrade removed filezilla on purpose!)

James

---

### Post by wabbster on 2009-06-11
Command line worked, thanks. Don't know why the Add/Remove method didn't. I'm running 32-bit Jaunty. :-/

---

### Post by Chronon on 2009-06-11
So, it seems that apt-get and Synaptic both work but add/remove doesn't.  Weird.

---

### Post by mcdragon on 2009-06-19
I can confirm this as well, Add/Remove didn't work and command line through 
```
sudo apt-get install filezilla
```
does.

I have a 32-bit Ubuntu on a IBM Thinkpad T43.

---

### Post by jimmygo on 2009-06-23
This just happened for me also. Relatively fresh install of 9.04, 32 bit, add/remove didn't work but CLI did. Odd.

---

### Post by RussellEngland on 2009-07-02
Fab!! The command line worked for me, thank you.

---

### Post by ajji on 2009-07-21
CLI worked for me. :KS

---

### Post by Eeve on 2009-09-17
Ooo this was very helpful. Thank you.

Has anyone told the Filezilla folks about this?

---

### Post by teward on 2009-10-28
I'd betcha it's a glitch within the Add/Remove system, and not the Filezilla people's fault.

Perhaps this is a bug within the Add/Remove feature where it's not differentiating between the 32-bit and 64-bit versions?

**EDIT: CLI worked, not Add/Remove.  32-bit Jaunty, installed as dual-boot config alongside WinXP, on a Dell Latitude E6500 Laptop. ***

---

### Post by ceciliaFX on 2009-12-31
btw, why is it that my installed Filzilla (3.1.2) tells me I have the lastest version but the [site]("http://filezilla-project.org/") claims the newest is 3.3.1-rc1  ???

if I type "sudo apt-get install filezilla" in a terminal it tells me I have the latest version.

it works so I'm fine with what I have, i'm just confused about this

---

### Post by rahul_bhise on 2010-03-09
while doing it through add/remove it told me it could be only installed on computers other than (i386). but this CLI command did work.

---

### Post by kikloo on 2010-04-22
Hello,

Latest version of Filezilla is: 3.3.2.1 where as in Ubuntu Software Center it says: 3.2.7.2. I just want to know how to install the latest version ?

Thanks.

---

