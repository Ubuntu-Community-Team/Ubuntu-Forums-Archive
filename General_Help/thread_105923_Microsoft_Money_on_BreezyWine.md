---
title: "Microsoft Money on Breezy/Wine"
date: 2005-12-19
forum: General Help
---

### Post by Oldan on 2005-12-19
I've been trying to install Ms-Money 2004 on my Breezy installation. It fails.

Wine is installed (version 200507xx).
I am able to run [ies4linux ]("http://www.tatanka.com.br/ies4linux/") and install IE 6.0. However, this doesn't mean that the Money install program is able to find IE. In fact, it finds nothing and excutes the IE 6.0 install (which fails).

According to this (probably old) [documentation]("http://appdb.winehq.org/appview.php?versionId=2728"), I should have DCOM98 and IE installed first. Well, that doesn't work. The DCOM install comes back with the joyful message that there's already a newer version of DCOM installed... do I really want to continue?

If anyone has any hints and tips on how to get Ms-Money on Wine in my install, that'd be GREAT!

thanks,
--Oldan

---

### Post by cstudent on 2005-12-19
I can't help you with Wine or MS Money. I haven't used either. I was a Quicken user in my past Windows life. I tried a couple of the free personal financial programs, kMyMoney and gnucash. They were ok, but I found one called Moneydance which I was satisfied enough with to  start using with Ubuntu. Moneydance is proprietary and cost about $30 to register it, but you can download and try it out for free. I think you can import your MS Money info over. It couldn't hurt anything to try if you desired. You can find Moneydance at [http://www.moneydance.com/](http://www.moneydance.com/)

---

### Post by Oldan on 2005-12-19
[QUOTE=cstudent]Moneydance is proprietary and cost about $30 to register it, but you can download and try it out for free. I think you can import your MS Money info over. It couldn't hurt anything to try if you desired. You can find Moneydance at [http://www.moneydance.com/](http://www.moneydance.com/)[/QUOTE]
Yeah, I liked what I saw of Moneydance. The fact that I can run it under Windows as well as UNIX was a definite plus. The only hitch is my bank, Wachovia, doesn't support it. From the look of the replies in the forums (fora?) it appears that they don't intend to either. :mad: 

Since I already own a copy of MsMoney, I thought it would be an easy thing to slip it into a WINE-enabled system. Not so!

One fellow at work suggested that I run Windows in a VMWare session... now **that's** over kill if I ever heard it.

--Oldan

---

### Post by cstudent on 2005-12-19
I hope you can find an easier solution. I can certainly understand if you already have MS Money setup the way you like. And especially since it is near year end. But I'm glad the subject came up. When I went to grab the link for Moneydance I saw where I was entitled to a free upgrade to the 2006 version. So I grabbed it for myself. :)

---

### Post by wassim1980 on 2005-12-22
Moneydance does look pretty interesting and I think I will give it a whirl tonight when I get back home. It would be great to get Microsoft Money on Wine, that's the only thing that keeps me from using Ubuntu completely as my OS at home.

---

### Post by Roman27 on 2005-12-22
I use Money 2004 as well.  I wound up installing Windows XP in a VMWare session in order to use it.  It's the one thing that still keeps me bound to Windows.  Not even Crossover Office 5.0 supports running MS Money in Linux.  :-(

I've looked at Moneydance too.  I even downloaded it and installed it.  But the install is very strange.  It must not be made to install in Ubuntu.  There was no menu icon for it and it installed itself in a directory that nothing else was installed into.  I think it was /opt or something.

cstudent, is there a guide on how to install Moneydance in Ubuntu?

---

### Post by Oldan on 2005-12-22
[QUOTE=Roman27]I use Money 2004 as well.  I wound up installing Windows XP in a VMWare session in order to use it.  It's the one thing that still keeps me bound to Windows.  Not even Crossover Office 5.0 supports running MS Money in Linux.  :-([/QUOTE]

Not hopeful.

[QUOTE=Roman27]I've looked at Moneydance too.  I even downloaded it and installed it.  But the install is very strange.  It must not be made to install in Ubuntu.  There was no menu icon for it and it installed itself in a directory that nothing else was installed into.  I think it was /opt or something.

cstudent, is there a guide on how to install Moneydance in Ubuntu?[/QUOTE]

You have to first install Blackdown Java Runtime.
Then you can run the installer shell script. It installs in the standard places but you're right, it doesn't create an icon (probably because it's the same installer used for KDE as well).

You might consider running "moneydance" from a terminal window. That works.

--Oldan

---

