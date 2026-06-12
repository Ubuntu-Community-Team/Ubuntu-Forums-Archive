---
title: "Kiten in Hoary"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Psimon on 2005-10-17
Is there a fix for the bug that stops Kiten loading in Hoary?

I know the problem has been fixed in Breezy, but I can't upgrade because I can't configure Japanese input (which is essential for me) in Breezy.

If anyone got it working I'd appreciate any help.

---

### Post by GoldBuggie on 2005-10-18
Don't know about kiten and such but japanese input just follow this -> [html]http://www.ubuntuforums.org/showthread.php?t=69694[/html] 
I'm sitting here in Japan at the moment and I'm real happy I got it to work before I left.

PS. I wonder if one needs to apply this how-to to 5.10 How-To page as well. DS.

---

### Post by drkeuk on 2005-10-18
Japanese input works in breezy, even if SCIM doesn't. Try uim as explained in [http://www.ubuntuforums.org/showthread.php?t=76985](http://www.ubuntuforums.org/showthread.php?t=76985) . It worked flawlessly for me.

---

### Post by GoldBuggie on 2005-10-18
/me scratches head...what do you mena S(C/K)IM does not work? It works for me. &#35211;&#19990;&#12387;&#12390;&#19979;&#12373;&#12356;

---

### Post by kairu0 on 2005-10-18
Are you using Hoary or Breezy?

If you have a working 1.0.2 version of SCIM in Breezy then you are really special. In every instance I've tried SCIM segfaults.

---

### Post by GoldBuggie on 2005-10-18
As I wrote that I had beta2 of KDE..maybe that helped...but since I have a seg fault of another app I'm guessing this is a major prob.

---

### Post by GoldBuggie on 2005-10-18
Maybe these will help the problem?
[http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/)

---

### Post by Psimon on 2005-10-18
Thanks to all for your responses. 

I've actually tried all the various advice recommended to install SCIM and had no luck. I also had the segmentation fault. Compiling it didn't install the configuration GUI and I couldn't bring up Anthy etc. UIM worked in some apps but not all, and I just don't have the time to persevere.

So it looks like I'll stick with Hoary, which is excellent. Kiten is the only problem.

I've always had trouble with various asian language support (I switched from Mandriva to Kubuntu for that reason), and I think it's something which should be given a higher priority. Surely it's essential that some form of input engine can easily be installed.

I notice someone has posted in tha ideas pool that SCIM should be the default input engine in Ubuntu. Let's hope so.

---

### Post by kairu0 on 2005-10-19
I am a UIM person myself, but if SCIM were made the default input method perhaps it would be given better support and then would become more useable.

More importantly, having an input method ready on your first boot would make Ubuntu a lot easier for many people.

---

### Post by delphi on 2005-10-19
[QUOTE=Psimon]
I notice someone has posted in tha ideas pool that SCIM should be the default input engine in Ubuntu. Let's hope so.[/QUOTE]

You can get SCIM (and scim-anthy) with Japanese support out of the box already - see Ubuntu-ja download page: [http://www.ubuntulinux.jp/download/](http://www.ubuntulinux.jp/download/)

---

### Post by Psimon on 2005-10-21
[QUOTE=delphi]You can get SCIM (and scim-anthy) with Japanese support out of the box already - see Ubuntu-ja download page: [http://www.ubuntulinux.jp/download/](http://www.ubuntulinux.jp/download/)[/QUOTE]


Thanks for the tip.

I installed the Japanese Ubuntu download and Japanese input works in every application. It installed by default and there was no need to configure it. As I prefer KDE to Gnome, I then downloaded and installed all the KDE packages. In Gnome, SCIM doesn't work in KDE apps but when I logged into KDE it worked in everything.

So if you need Japanese input, downloading the Japanese version of Ubuntu seems to be the best bet. The install is all in Japanese but it's easy enough to follow if you can read hiragana/katakana, or have installed Ubuntu before as the procedure is exactly the same.

The only problem I've found is the segmentation fault in realplayer but there's a fix for that on the SCIM website.

---

