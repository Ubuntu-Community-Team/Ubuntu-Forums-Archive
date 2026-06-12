---
title: "Installing gparted..."
date: 2009-01-07
forum: General Help
---

### Post by hayden78 on 2009-01-07
hi. 

I just tried to install gparted , but I am unsure of how to install it. Could someone please give me some pointers? I realize this could be looked up easily by google, but for some reason I can't get it working. This has something to do with another problem I had, with partitioning a usb stick. 
:confused:
I'm not quite sure what else to tell you, so if you have any questions, I will answer to te best of my ability. Thanks in advance. 

I left a link to a snapshot of what I have , concerning gparted, below.  Just so you know, I tried apt-get, but couldn't connect for some reason, even though I have an obvious connection, and I am not using a proxy. Oh, and I am certain my sources.list is correct, got it from a website that specified my version of ubuntu. 

[http://i42.tinypic.com/33za1ia.jpg](http://i42.tinypic.com/33za1ia.jpg)

---

### Post by bumanie on 2009-01-07
You should only need to do > sudo apt-get install gpartedThen you will find it under System --> Administration --> Partition Editor. You could also go to the [gparted site]("http://gparted.sourceforge.net/download.php") and download the dedicated live cd for gparted.

---

### Post by fooman on 2009-01-07
look in system > administration > partition editor (that is gparted)


edit: again i am too slooow

---

### Post by hayden78 on 2009-01-07
thank you for replying. 


I tried that, this is what I got..


"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate"


:(

---

### Post by The Cog on 2009-01-07
Try 
> sudo apt-get update
sudo apt-get install gparted

---

### Post by fooman on 2009-01-07
try in synaptic...system > administration > synaptic package manager

in the toolbar choose settings > repositories

when it opens,  click the "ubuntu software" tab....make sure the first 4 choices are checked (main - universe - restricted - multiverse)...then close that window.

you should see a warning saying that the repos have changed...close that window as well.

back in synaptic,  click "reload"....then search for "gparted"

---

### Post by sPiN1 on 2009-01-07
If you're going to mess around in gparted I would highly suggest doing so on the live disc.

---

### Post by hayden78 on 2009-01-07
> **fooman said:**
> look in system > administration > partition editor (that is gparted)


edit: again i am too slooow


Thanks , but it's not in system>admin

nowhere to be found. I know it's not a bad copy of ubuntu, got it right from the company, and I also ran the cd error check thing, before installing. Nor have I deleted/removed anything. 

This is weird.

---

### Post by hayden78 on 2009-01-07
Hm. it is stuck on "0% [Connecting to 70.113.126.18 (70.113.126.18)] [Connecting to 70.113.126.18 (". Same as before. 

Notice how before it said it may not be available from that source? Could it be my sources.list is wrong? Perhaps if I posted my sources.list, someone could tell me if I have it wrong? I know, and I am sorry.. know its got to be a pain. 


Wait... now it is saying it "failed to fetch".. on a bunch of sources. Hm.

---

### Post by hayden78 on 2009-01-07
Bah. It's got to be just a crappy install, or something. I cannot even get synaptic package manager going, or a few other administrator things. I click on them , see them 'starting up'... and then nothing. ugh. 


I did also find "Gnome Partition Editor", in a folder. Though, it does not have an icon like I'd expect. The icon for it is a piece of paper.

---

### Post by sPiN1 on 2009-01-07
> **hayden78 said:**
> Bah. It's got to be just a crappy install, or something. I cannot even get synaptic package manager going, or a few other administrator things. I click on them , see them 'starting up'... and then nothing. ugh. 


I did also find "Gnome Partition Editor", in a folder. Though, it does not have an icon like I'd expect. The icon for it is a piece of paper.

It seems to have bad installation at times, I would recommend a re installation if you don't have anything important on it.

---

### Post by hayden78 on 2009-01-07
When I go into terminal and type in 'sudo wherefileis' I get:


"/Desktop/synaptic.desktop' 
/home/hayden/Desktop/synaptic.desktop: 1: [Desktop: not found
/home/hayden/Desktop/synaptic.desktop: 2: Package: not found
/home/hayden/Desktop/synaptic.desktop: 3: Name[ar]=&#1605;&#1583;&#1610;&#1585;: not found
/home/hayden/Desktop/synaptic.desktop: 4: Name[be]=&#1050;&#1110;&#1088;&#1072;&#1118;&#1085;&#1110;&#1082;: not found
/home/hayden/Desktop/synaptic.desktop: 5: Name[be@latin]=Kira&#365;nik: not found
/home/hayden/Desktop/synaptic.desktop: 6: Syntax error: "(" unexpected"


>=O

---

### Post by hayden78 on 2009-01-07
Figures. I was sort expecting this to go wrong.



I think maybe I'll just forget it. 

thank you for the help.

---

### Post by hayden78 on 2009-01-07
AHHH!

How is it possible the usb disc creator is writing to the usb, yet it cant be mounted?  I thought it if couldn't read it, it couldn't read it. Now if only Unetbootin would let me do that same as the usb disc creator. Right now it is creating a usb start up disc, does this mean it will change the file system????

---

