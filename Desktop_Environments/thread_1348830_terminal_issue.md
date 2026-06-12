---
title: "terminal issue"
date: 2009-12-07
forum: Desktop Environments
---

### Post by stlsaint on 2009-12-07
i installed kde over gnome (ubuntu 9.10) all has been well until today when i open up my terminal using (terminator) and it opens me up to /home/stlsaint/Documents on default. i dont change anything and it goes to that location on its own...nothing is edited in my .bashrc (btw i am using zsh and bash and both yield same results). 
Any ideas?

---

### Post by adaucourt on 2009-12-07
> **stlsaint said:**
> i installed kde over gnome (ubuntu 9.10) all has been well until today when i open up my terminal using (terminator) and it opens me up to /home/stlsaint/Documents on default. i dont change anything and it goes to that location on its own...nothing is edited in my .bashrc (btw i am using zsh and bash and both yield same results). 
Any ideas?

not sure if this applies but you can take a look:
[http://ubuntuforums.org/showthread.php?t=872579](http://ubuntuforums.org/showthread.php?t=872579)

---

### Post by stlsaint on 2009-12-07
> **adaucourt said:**
> not sure if this applies but you can take a look:
[http://ubuntuforums.org/showthread.php?t=872579](http://ubuntuforums.org/showthread.php?t=872579)

Thanks for reply...i tried all the ideas from that post you gave but none worked.

---

### Post by apmcd47 on 2009-12-07
In konsole, select "Settings/Edit Current Profile..." and in the resulting dialog, under "General" tab, check your initial directory.

Andrew

---

### Post by drubin on 2009-12-08
> **apmcd47 said:**
> In konsole, select "Settings/Edit Current Profile..." and in the resulting dialog, under "General" tab, check your initial directory.

Andrew

Odd that this value could carry over to Terminator, and tty's! though?

---

### Post by stlsaint on 2009-12-08
> **apmcd47 said:**
> In konsole, select "Settings/Edit Current Profile..." and in the resulting dialog, under "General" tab, check your initial directory.

Andrew

There is no general tab in kde (from what i can find) but my home dir has already been proven as being /home/stlsaint

thanks for reply tho

---

### Post by Gen2ly on 2009-12-08
System Setttings > About Me > Paths   ?

If you want that doesn't work you can directly tell bash where to go in your ~/.bashrc

cd $HOME

---

### Post by stlsaint on 2009-12-08
> **Gen2ly said:**
> System Setttings > About Me > Paths   ?

If you want that doesn't work you can directly tell bash where to go in your ~/.bashrc

cd $HOME

my paths are correct and bashrc is correct. though i am in zsh.
thanks for reply

---

### Post by drubin on 2009-12-08
[http://techbase.kde.org/KDE_System_Administration/KDE_Filesystem_Hierarchy#KDEHOME](http://techbase.kde.org/KDE_System_Administration/KDE_Filesystem_Hierarchy#KDEHOME) 

Please post the output of echo $KDEHOME :)

[https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/364197](https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/364197)

---

### Post by stlsaint on 2009-12-08
> **drubin said:**
> [http://techbase.kde.org/KDE_System_Administration/KDE_Filesystem_Hierarchy#KDEHOME](http://techbase.kde.org/KDE_System_Administration/KDE_Filesystem_Hierarchy#KDEHOME) 

Please post the output of echo $KDEHOME :)

[https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/364197](https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/364197)

that returns nothing but a blank line then back to prompt.

---

### Post by drubin on 2009-12-08
> **stlsaint said:**
> that returns nothing but a blank line then back to prompt.

O well there goes that idea. If that isn't set then I don't see that as being the issue.

---

### Post by SkonesMickLoud on 2009-12-08
> **stlsaint said:**
> my paths are correct and bashrc is correct. though i am in zsh.
thanks for reply

Then put it in ~/.zshrc

---

### Post by stlsaint on 2009-12-08
> **SkonesMickLoud said:**
> Then put it in ~/.zshrc

thanks for response
but my zshrc is also fine for path.

---

### Post by stlsaint on 2009-12-09
i believe i have narrowed down issue some more. I opened up regular terminal (not terminator) and i was started at correct location (/home/stlsaint) so i figure it has to do with terminator!

---

