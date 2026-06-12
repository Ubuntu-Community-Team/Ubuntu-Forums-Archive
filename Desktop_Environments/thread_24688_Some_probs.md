---
title: "Some probs"
date: 2005-04-08
forum: Desktop Environments
---

### Post by aces170 on 2005-04-08
Hi folks I have the Warty version 4.10 and have installed the x-86 version. The prob is I enabled the root account, but I cant play Mp3's, cant mount Windows, cant Install XMMS.

I tried the commands given here ;
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

1. What are repositories ?
2. I use the apt get command for everything and I get Package not found.
3. I tried to install XMMS, I wrote ./configure and it gave me C compiler not found...
4. I tried mounting Windows HDD ( was listed /dev/hddb in the device manager.) Got a system busy or blocked message.

---

### Post by bored2k on 2005-04-08
1. Repositories are the links where you get your files from. Here in Ubuntu, we don't search the web for an application, we open something called Synaptic and search them there.
2. If you what is said [here](http://ubuntuguide.org/#extrarepositories) you will have better luck finding items.
3. After step two, go to System > Administration > Synaptic Package Manager [your user password], and search for XMMS and/or any application you want.

4. This one is a bit more complicated. What filesystem is your drive on? Fat?NTFS?

---

### Post by aces170 on 2005-04-08
[QUOTE=bored2k]1. Repositories are the links where you get your files from. Here in Ubuntu, we don't search the web for an application, we open something called Synaptic and search them there.
2. If you what is said [here](http://ubuntuguide.org/#extrarepositories) you will have better luck finding items.
3. After step two, go to System > Administration > Synaptic Package Manager [your user password], and search for XMMS and/or any application you want.

4. This one is a bit more complicated. What filesystem is your drive on? Fat?NTFS?[/QUOTE]
 Well this is for my comp at home, rt now dont have a Net connection at my place. So will I need to download the repositories ?

Also Prob No 3 about the C compiler How do I go abt that ?
I have an NTFS partioned Windows....

---

### Post by Leif on 2005-04-08
Yes, you will need to download them. If not having a connection at home is a temporary issue, I'd say leave this until you get it back. Otherwise, you will have to download the .deb files from somewhere else and then install them using dpkg -i back at home.

---

### Post by aces170 on 2005-04-08
[QUOTE=Leif]Yes, you will need to download them. If not having a connection at home is a temporary issue, I'd say leave this until you get it back. Otherwise, you will have to download the .deb files from somewhere else and then install them using dpkg -i back at home.[/QUOTE]

How and From where do I download the packages. Also If I have XMMS package why cant I install it ?, my friend informed me I will need to load the C complier from the Ubuntu CD... How do I do that ?

---

### Post by aces170 on 2005-04-09
Ok, Folks from where can I download the Repositories ? Also I have downloaded XMMS, and I tried to install as per the instructions provided in the readme, wen I typed ./configure I got an error C compiler not found ?

Pls Help me out.

---

### Post by Leif on 2005-04-09
You need to install gcc using synaptic.

---

### Post by aces170 on 2005-04-09
How do I do that ?

PS: I am a newbie.

---

### Post by Leif on 2005-04-09
Click System->Administration->Synaptic. Search for gcc, mark it for installation and apply.

Alternatively, start a terminal and type "sudo apt-get install gcc"

---

### Post by aces170 on 2005-04-09
[QUOTE=Leif]Click System->Administration->Synaptic. Search for gcc, mark it for installation and apply.

Alternatively, start a terminal and type "sudo apt-get install gcc"[/QUOTE]
 Umm Sorry to bother ya again but I dont have a net connection at Home, so will the apt get command work ?

If yes then I guess the Ubuntu CD should be inserted ?

---

### Post by Leif on 2005-04-09
I think gcc should be on the disc, so go ahead and try it.

---

### Post by aces170 on 2005-04-11
Hi,

Thanx I managed to install GCC , but now get an error Gtk 2.2 Lib not found. What next ?

---

### Post by Leif on 2005-04-11
I'm guessing it means you need libgtk2 (search for gtk in synaptic), but this has a ton of packages that depend on it, so you may have to upgrade these too.

---

