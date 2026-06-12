---
title: "Plan for YAST like configuration tool?"
date: 2005-03-25
forum: Desktop Environments
---

### Post by vvu on 2005-03-25
Great review of Suse and features...

I was just reviewing this article - 

[http://www.flexbeta.net/main/articles.php?action=show&id=88&perpage=1&pagenum=3](http://www.flexbeta.net/main/articles.php?action=show&id=88&perpage=1&pagenum=3)     =D> 

I wondered if this type of configuration tool will be incoporated into Ubuntu or Kubuntu - anyone know?


If so, when?

Thanks.

---

### Post by Jad on 2005-03-25
Well, from what I can understand of Ubuntu concepts, they will not develop any application from scratch but they will participate to enhance existing applications

so I don't think so.

---

### Post by vvu on 2005-03-25
Oh yess!  Novell I just read released their YAST tool under GPL!  Now we can incorporate it!

[http://news.com.com/2100-7344_3-5175682.html?tag=nefd_top](http://news.com.com/2100-7344_3-5175682.html?tag=nefd_top)


How do we get the Ubuntu developers to look at this seriously for incorporation?!

---

### Post by arctic on 2005-03-25
i don't think they will incorporate it. and that is the best thing they can do. i guess you don't know anything about yasts problematic compiling procedure...

---

### Post by vvu on 2005-03-25
Sorry...not a programmer a newbie - but it was a recommendation for a tool - UNIFIED tool to administer the system as a whole.  Maybe Ubuntu support will create something better, but it was a recommendation because from USER perspectrive, it it a good tool to simplify and encourage adoption of  Ubuntu faster - even in businesses (not just hobbyist).  Again, this is not for developers, but for USER acceptance.

---

### Post by arctic on 2005-03-25
yes, i do understand that but is the user willing to take the risk of having his system more instable than necessary? i once ran on suse and yast wrecked my box three times irreparably. well, i knew how i could get my system back running again as i am quite experienced with linux systems but if i were an average user, i would have been depressed for a at least a week.

the more you pack together into one program, the higher is the risk of a fatal error on your system.

---

### Post by vvu on 2005-03-25
Just a newbie and user perspective...I am not saying take the YAST code, but to modify it and make something Ubuntu could use.  I love Ubuntu and its simplicity so far, but I want to go to a client and say...check this out - it even has these things for YOU...

Afterall, most of the people I want to go to with this are  my MS clients and MS is killing Linux in general because of simplified and unified interface.  Let's not talk aout which product is superior.  There's a reason it's easier to find a Windows Admin (you can get a dummy) whereas harder to get a Linux admin (more skilled).  there's also a reason why companies buy MS - not just marketing, but the product is so EASY that it takes someone with no skills to get it up and running - not neccessarily correct either.

My point, I want a tool that shows the SMB and Enterprise clients a reason they can switch - ease of use - cause right now, there are many ways to do things in Linux (great) but for the general public - they want a STANDARD way and simplified way.  Microsoft = MMCs, Red Hat = ... , etc...

Lastly, I am a MS Consultant and I get this all the time - "we chose this product because it is better, easier, less work, etc etc).  The management and administration makes a HUGE difference.

---

### Post by Buffalo Soldier on 2005-03-25
Prefer the way it's being done in Ubuntu. I like Ubuntu's way of keeping things separate under Preferences and Administration menu.

---

### Post by vvu on 2005-03-25
Sir...this is not the Administration for KDE or computer system, but for Services such as DNS, Samba, LDAP, etc...I guess I'm not such a newbie...even if this is my first!  YAYAYAY!

---

### Post by Buffalo Soldier on 2005-03-25
Opss. Didn't notice a KDE discussion. My bad.

Anyway, just out of curiosity, so please don't flame me. There are no integrated configuration tools for DNS, Samba, LDAP and etc ic KDE?

---

### Post by vvu on 2005-03-25
Nope, closest thing is via Webmins

---

### Post by ACK!! on 2005-03-25
[QUOTE=vvu]Sir...this is not the Administration for KDE or computer system, but for Services such as DNS, Samba, LDAP, etc...I guess I'm not such a newbie...even if this is my first!  YAYAYAY![/QUOTE]

Ok, I am not a newbie been using Unix for nearly ten years and linux for eight.

First, my Suse rant.  You have this distro right?  For a KDE fan, its even a damn slick distro each part of the Yast configuration tool is embedded in that monster mess of options that is the KDE Control Center.  All very integrated and very slick mind you.

But it comes at a terrible price for the advanced user.  I am surprised this has not hit other people or does not come up as the first reply to every Suse Novell centered thread.  It has this horrible script that runs after almost every changed made from YaSt.  It is called Suseconfig and it is pure evil.  Its this script that runs and changes stuff all over the system.  It can change permissions on files or change configs on the fly to "fix " things that you have broken.  

Unix was NOT designed to prevent you from doing stupid things because that would prevent you from doing clever things.  That quote btw is not mine.  

Ubuntu uses a host of gtk2 and gnome configuration tools some from Ximian like the CUPS tool and some from outside sources like firestarter for firewalls available in universe I believe or gnome-system-tools that come by default.  

Now, Ubuntu is obviously missing a program for editing services like run-level-admin but many others are included.  This approach is very divorced in a sense from the distro.  This tools exist outside of the world of Ubuntu and this is a good thing.  

The linux world has become too dependant on distro specific ways of doing things from configuring the systems to package formats to well .... too many things.  That is why for example I like Autopackage and use it whenever possible despite the pure greatness of the deb format for creating and maintaining core system packages.  I look forward to a day when my system to give another example comes with just the barebones like Ubuntu is now but all the outside packages everyone installs comes on a format I could feasibly install on any distro.  I hope that is coming.

Any gnome based system can use firestarter or the CUPS tool or HAL or gnome-system-tools.

There is a package for the maintaining of directories, user, authentication, mail preferences and even samba share access.  

It is called Directory Administrator available here --  

[http://diradmin.open-it.org/index.php](http://diradmin.open-it.org/index.php) 

All any distro needs now is a druid to download all the necessary packages in their format (deb or rpm) and do the initial setup which really consists of creating one directory and one user but getting the authen part of the OpenDirectory like solution is really the hardest part.  Kerberos and PAM and all that working with LDAP and SAMBA that is.  Anyway, after the initial setup all one has to do is maintain the system with Directory Administrator and you are set. 

Who will make the setup tool needed?  I hope it will be someone who is not tied down hard by one packaging format or one distro.  That is my hope.

Apple packaged a lot of these pieces in a product it calls OpenDirectory and Novell is pushing their e-Directory solution combined with LDAP and Samba.

Hopefully the truly open world of Free Open Source Software can soon follow suit.

---

### Post by denzilla on 2005-03-25
I am a Linux newb and know nothing, but I will say this. I went out and bought SUSE 9.2 at Christmas time and although I liked the look, never really got it working right. It was always some stupid glitch. YAST as mentioned above, wrecked my install several times. I understand that it might not've been so bad if I had some experience  with linux, but I feel alot of those issues should've never happened in the first place. YAST was supposed to simplify the updating process and instead it created kernel dependency conflicts. 

I'm toying with Kubuntu right now and it just feels right. This is going to be the distro  I stick with. I love the KDE GUI and Kynaptic hasn't screwed the machine up once. YAST can stay where its at!

---

### Post by vvu on 2005-03-25
Again...YAST is not like synaptic or Kynaptic or KDE Control Center - the piece I was referring to was Network Service Management...sorry I give  :-#

ACK...thanks for the link for DIRADMIN - just the tool I was hoping for (part of it anyhow)!  YAYYYYY!  =D>

---

### Post by ACK!! on 2005-03-26
[QUOTE=vvu]Again...YAST is not like synaptic or Kynaptic or KDE Control Center - the piece I was referring to was Network Service Management...sorry I give  :-#

ACK...thanks for the link for DIRADMIN - just the tool I was hoping for (part of it anyhow)!  YAYYYYY!  =D>[/QUOTE]

DIRADMIN is good for maintaining these services but does not help in the complicated matter of setting them up in the first place.

I set up a NIS configuration years and years ago and i would kill for a secure authentication service that was as simple to set up but was of course secure in a real way.  Hell I thought about NIS-ssh but then again no ones uses NIS not even wrapped in a secure shell anymore.  

There are a number of sites that go into detail about setting up LDAP with Kereberos authen and mixing in Samba as well.  

If you can get all that up then Directory Administrator is good for setting up all the users and stuff after.  

But it needs one created directory and one user and that means all the other stuff I mentioned above has to be in place.

---

