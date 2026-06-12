---
title: "Battle to install Wesnoth"
date: 2006-09-08
forum: Gaming &amp; Leisure
---

### Post by jimw on 2006-09-08
I'm using Dapper, and I've discovered the Battle for Wesnoth.  What's available from Synaptic is 1.0.2.  However 1.1.8 has been out for about a month, and seems to be about to become 1.2.

I've found it on: 
 
[http://ftp.us.debian.org/debian/pool/main/w/wesnoth/](http://ftp.us.debian.org/debian/pool/main/w/wesnoth/)

but I haven't been able to hook that into my sources (let's just say I have only a hazy idea of how to do things.)

I downloaded the tarball, extracted it, did all the things with ./configure, make, and make install, plus a make clean for good measure.

Unfortunately, no executable file seems to have been produced.

Anybody got any hints as to what I might have done wrong?

JimW

---

### Post by Perfect Storm on 2006-09-08
When compiled the command to start Wesnoth is **wesnoth**

If you had all the required libs (you can check it when running ./configure) it should be straight forward.



I wouldn't recommend adding Debian to your sourcelist. Furthermore newer versions of libs might be required to run Debian .deb version of wesnoth.

---

### Post by jimw on 2006-09-08
> **Artificial Intelligence said:**
> When compiled the command to start Wesnoth is **wesnoth**

If you had all the required libs (you can check it when running ./configure) it should be straight forward.



I wouldn't recommend adding Debian to your sourcelist. Furthermore newer versions of libs might be required to run Debian .deb version of wesnoth.

Thanks for your trouble. 
 I just went through the whole process this morning, and a very long one it was, too.

After doing a sudo update to be sure, I tried putting in 'wesnoth' (without the quotes, of course), and got the following error message: 

bash: /usr/games/wesnoth: No such file or directory.

Obviously, it didn't install the game, at least not in /usr/share/games.  

The problem with using the present Ubuntu version of wesnoth is that many of the campaigns for the game were written on more advanced versions, and will not work on 1.0.2

Any other suggestions?

---

### Post by Perfect Storm on 2006-09-08
I've written a howto on howto compile wesnoth: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)

---

### Post by jimw on 2006-09-08
> **Artificial Intelligence said:**
> I've written a howto on howto compile wesnoth: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)


Had to rush off this aftrernoon,so I left it with the situation as it had been, wesnoth-1.1.8 supposedly loaded, but apparenty undiscoverable.

Came home this evening and turned the computer on.  Went into terminal and typed 'wesnoth'.  The beginning screen was a whole different style of graphic, and it informed me it was verifying cached.

These two things told me I almost certainly had a different version, and indeed, when it finished loading, there it was version 1.1.8.

Only thing I can think of is that this version required me to turn the machine off before it was actually installed.

Is this likely?  (Worse yet, is it something I ought to have known?):) 

JimW

---

### Post by Perfect Storm on 2006-09-09
Did you uninstall the previous version first?

---

### Post by jimw on 2006-09-09
> **Artificial Intelligence said:**
> Did you uninstall the previous version first?

Yup.

JimW

---

### Post by mikl on 2006-09-30
> **jimw said:**
> I'm using Dapper, and I've discovered the Battle for Wesnoth.  What's available from Synaptic is 1.0.2.  However 1.1.8 has been out for about a month, and seems to be about to become 1.2.

I've found it on: 
 
[http://ftp.us.debian.org/debian/pool/main/w/wesnoth/](http://ftp.us.debian.org/debian/pool/main/w/wesnoth/)

but I haven't been able to hook that into my sources (let's just say I have only a hazy idea of how to do things.)

I downloaded the tarball, extracted it, did all the things with ./configure, make, and make install, plus a make clean for good measure.
I know this is old, but in case you haven't figured it out yet:
Why bother with compiling it?
I just downloaded the .debs from the link you posted and did sudo dpkg -i wesnoth* on the dir where i downloaded them - and now, I have a perfectly working Wesnoth 1.1.10 :)

(That's on edgy, btw, but it might work on dapper as well)

---

### Post by mikl on 2006-10-07
This also works with Wesnoth 1.1.11

---

### Post by mikl on 2006-12-02
And 1.1.12 :D

I just went to [http://ftp.us.debian.org/debian/pool/main/w/wesnoth/](http://ftp.us.debian.org/debian/pool/main/w/wesnoth/) and downloaded all files matching /.*_1.1.12-1_(i386|all)/ (replace i386 with your arch) with the DownThemALL Firefox extension (enable regular expressions)

That gives me these files:
```
-(mikl@ariel)-(6/pts/0)-(~/Desktop/Downloads)-
-($ ls | grep wesnoth
wesnoth_1.1.12-1_i386.deb
wesnoth-data_1.1.12-1_all.deb
wesnoth-editor_1.1.12-1_i386.deb
wesnoth-ei_1.1.12-1_all.deb
wesnoth-httt_1.1.12-1_all.deb
wesnoth-music_1.1.12-1_all.deb
wesnoth-server_1.1.12-1_i386.deb
wesnoth-trow_1.1.12-1_all.deb
wesnoth-tsg_1.1.12-1_all.deb
wesnoth-ttb_1.1.12-1_all.deb
wesnoth-utbs_1.1.12-1_all.deb
```

Then just run ```
sudo dpkg -i wesnoth*.deb
``` where you downloaded the file, and bam!, you've got the newest version of Wesnoth, and when you upgrade to Feisty or Wesnoth gets packported, you'll automatically get the latest version.

---

