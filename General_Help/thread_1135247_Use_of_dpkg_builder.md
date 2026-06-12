---
title: "Use of dpkg builder"
date: 2009-04-24
forum: General Help
---

### Post by ivan1979 on 2009-04-24
Hello, 
it's my first post and then at least a greeting, I am a windows programmer but I'm trying (with some success) to do some porting of my works on my Linux.

I hope you can help: 
Using dpkg I created (excellent guide at https: / / wiki.ubuntu.com / PackagingGuide / Basic? action = show & redirect = HowToBuildDebianPack ... for new Ubuntu packages) 
successfully completed a distribution package .deb of my project and i can install it correctly, but to run it (it is a java project, then. jar) I have to execute, of course, from the shell the command *java-jar NomeFile.jar*.

Now I'd like: 
- to add automatically, when installing, my program on menu shorcourt, for example in Application-> Programming, so that the user should not necessarily where you will find the jar and run it or shell. Is it possible? Can yuo help me? 

Thanks in advance. 
Ivan

---

### Post by Bender2k14 on 2009-04-24
I know it is possible. Several programs that I have installed from the repositories do this.  However, I don't know how to do this, but I will look into it.

---

### Post by Bender2k14 on 2009-04-24
I found [this script]("http://www.stchman.com/tools/filezilla/filezilla_install.sh") (on [this site]("http://www.stchman.com/tools_page.html")) which says that it creates a menu entry.

Does this help?

---

### Post by ivan1979 on 2009-04-24
Thanks.
I'll try and inform you.:)

---

### Post by ivan1979 on 2009-04-24
**Does this help?**

Yes, it did!
Thanks very much.
I had to modifiy some line of script and it worked, in particulare to execute a java jar it was enough to change the lines:

sudo echo "Exec=filezilla"  >> /usr/share/applications/filezilla.desktop 

in

sudo echo "Exec=nameofJar.jar"  >> /usr/share/applications/filezilla.desktop

and

sudo ln -s /opt/FileZilla3/bin/filezilla /usr/bin/filezilla

in

sudo ln /usr/lib/nameofJar.jar

Thanks
Ivan

---

### Post by Bender2k14 on 2009-05-11
I found [another page about creating menu items in Gnome]("http://ubuntufs.wordpress.com/2007/05/15/add-menu-items-in-gnome/"), so I thought I would post that link as well.

---

