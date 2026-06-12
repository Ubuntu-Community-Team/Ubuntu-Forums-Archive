---
title: "cannot install yahoo messenger"
date: 2005-12-13
forum: General Help
---

### Post by Tominator on 2005-12-13
I've tried qite a few times to install this messenger. I download the debian package from yahoo to my desktop and then I follow the directions but it will not install. When I click on the yahoo icon on my desktop, I get the message that the " Archive type not supported". I am running a recently installed 5.10 version of Ubuntu. Does anyone know how to handle this situation?

---

### Post by spincricket on 2005-12-13
why dont you use gaim?

---

### Post by Tominator on 2005-12-13
I gues because I'm a newbie and don't know how or what gaim is.

---

### Post by Tominator on 2005-12-13
I'm guessing gaim is a messenger, absolutely all of my online friends use yahoo though

---

### Post by teaker1s on 2005-12-13
gaim is a free messenger that works with aol/msn/yahoo and others
install with synaptic
sudo synaptic

---

### Post by Tominator on 2005-12-13
Thanks teaker, you are so right about the insufficient info thing, I am learning the hard way as well, lol.

---

### Post by cstudent on 2005-12-13
I downloaded and installed the Yahoo Messenger .deb file and got it to work.

Here is what I did:

In a terminal window enter: (leave the quotes out)

**"wget http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb"**

After it finishes downloading enter:

**sudo apt-get install libssl0.9.6** (this library was needed)

**sudo dpkg -i ymessenger_1.0.4_1_i386.deb**

After these packages are installed you can run Yahoo messenger from the terminal by entering:

**/usr/bin/ymessenger**

When I first ran it I had to fill out some setup info. The package is kind of old and the Gnome options did not give me an icon in my menu or on the desktop. I right clicked on the desktop and created a launcher. Named it Yahoo Messenger and entered the /usr/bin/ymessenger in the command box. You can hunt for an icon if you'd like. The laucher did work for me.

Now all that being said. Use Gaim. You can connect to Yahoo, MSN, AOL, ICQ, Google Talk, Jabber all at the same time. The drawback is you won't have voice conversations or web cam stuff, but that's not available in the Linux version of Yahoo Messenger either. 

Hope this helps.

---

### Post by RAOF on 2005-12-13
You will find gaim installed by default:  Applications->Internet->Instant Messaging (GAIM)

---

### Post by shane2peru on 2005-12-15
wow, great post!  I had to install ```
sudo apt-get install xlibs 
``` to get mine to work.  When you run the dpkg it will tell you what you are missing.  Too bad it still doesn't do video or voice?  Oh well.  At least it is yahoo!

Shane

---

### Post by rykel on 2005-12-16
hi friend,

does anyone of u know how i can get the windows version of yahoo messenger 7.0 to work? it is not becoz i don't have gaim, it is just tat i would like to listen to the yahoo radio stations while working like the way it is in windows xp... any idea? thanks!!

or can i listen to yahoo radio from rhythmbox/realplayer?

---

### Post by shane2peru on 2005-12-16
Rykel,

    I tried via Wine, but was not able to get it running.  It installed ok, but doesn't seem to run after that.  If anyone has it would be great to hear how! 

Shane

---

### Post by rykel on 2005-12-16
[QUOTE=shane2peru]Rykel,

    I tried via Wine, but was not able to get it running.  It installed ok, but doesn't seem to run after that.  If anyone has it would be great to hear how! 

Shane[/QUOTE]

no luck here... neither wine nor crossover would make it work; neither version 7.0 nor 7.5...

---

