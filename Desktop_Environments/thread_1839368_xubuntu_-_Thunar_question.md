---
title: "xubuntu - Thunar question"
date: 2011-09-05
forum: Desktop Environments
---

### Post by makitso on 2011-09-05
Hi, I am a ubuntu user but running xubuntu 11.04 to see how I like it.  

The biggest problem I have to date is the file manager (Thunar).  With Nautilus, I could view a folder with images and in icon view see the preview if .jpg, png, etc image files.  So, I want to do the same thing in Thunar.  However, in View in Icon mode I get the default image.  So, I installed Thunar-thumbnailers and Xfce4-goodies.  But, no help.  So, How do I do this?

Second question is, how to install themes in xubuntu?  I use theme packages in Ubuntu but I don't believe that will work in the shell.

Thanks in advance,

---

### Post by Toz on 2011-09-05
> **makitso said:**
> Hi, I am a ubuntu user but running xubuntu 11.04 to see how I like it.  

The biggest problem I have to date is the file manager (Thunar).  With Nautilus, I could view a folder with images and in icon view see the preview if .jpg, png, etc image files.  So, I want to do the same thing in Thunar.  However, in View in Icon mode I get the default image.  So, I installed Thunar-thumbnailers and Xfce4-goodies.  But, no help.  So, How do I do this?
Do you have tumbler installed? I don't have thunar-thumbnailers installed and have thumbnails with tumbler.

> Second question is, how to install themes in xubuntu?  I use theme packages in Ubuntu but I don't believe that will work in the shell.
Have a look at this link for information: [http://wiki.xfce.org/howto/install_new_themes]("http://wiki.xfce.org/howto/install_new_themes")

---

### Post by makitso on 2011-09-06
> Do you have tumbler installed? I don't have thunar-thumbnailers installed and have thumbnails with tumbler.

Yes, thunar-thumbnailers is installed.  This is a clean 11.04 install.  I just want to see the preview of the image file in the file browser.  Is there some step-by-step method to get this to work.  Or, should I try and get the answer on a thunar site?

---

### Post by Toz on 2011-09-06
Mine is a fresh 11.04 install and I _do not_ have thunar-thumbnailers installed. I _do_ have tumbler installed.

```

$ apt-cache policy thunar-thumbnailers 
thunar-thumbnailers:
  Installed: (none)
  Candidate: 0.4.1-3ubuntu1
  Version table:
     0.4.1-3ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/universe i386 Packages

$ apt-cache policy tumbler
tumbler:
  Installed: 0.1.21-0ubuntu1
  Candidate: 0.1.21-0ubuntu1
  Version table:
 *** 0.1.21-0ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/universe i386 Packages
        100 /var/lib/dpkg/status

```

And thunar thumbnails work. Can you confirm whether you have tumbler installed?

EDIT: See this link: [https://bbs.archlinux.org/viewtopic.php?id=116349]("https://bbs.archlinux.org/viewtopic.php?id=116349")

---

### Post by makitso on 2011-09-06
Toz,  a strange thing.  I was testing the viewing of thumbnail  files by looking at a folder in my home directory /home/me/.thumbnails/normal.  These are .png files and even when I converted one to .jpg still no preview.  Well then I copied one of the file to /home/me and then the preview showed!  This was after I removed thunar-thumbnailers.

So, I tried some other files /usr/share/icons etc and image thumbnails were viewed.  I have no idea what I stumbled into but I really appreciate your help.

---

