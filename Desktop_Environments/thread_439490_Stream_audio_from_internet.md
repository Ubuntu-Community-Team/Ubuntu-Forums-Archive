---
title: "Stream audio from internet"
date: 2007-05-10
forum: Desktop Environments
---

### Post by geek2330 on 2007-05-10
Hi all, new to Kubuntu and so far it is nice.

I am trying to listen to some radio stations that I listen to using my XP Pro with Media Player but am having many issues with finding the right stuff for Kubuntu.

First, when I go to this station and click on the "Listen Live" hyperlink on the top right hand corner, it keeps "loading" but nothing happens. Note that is looking for a pluggin that kubuntu can't install:

[www.webe108.com](www.webe108.com)

The other station is Latin music here:
[http://www.galaxia1380.com/Home.php](http://www.galaxia1380.com/Home.php)

then I click on the "Listen Galaxia 1380 Online" link on the right hand side.

I even tried using the streamtuner but no luck, specially for the 2nd station, tried adding a port (8000 and 8002) just to try but no luck...

Any help is appreciated.

---

### Post by diatribe on 2007-05-10
have you tried installing java for the first site?  also which browser are you using?
edit: for the second site, you may need to install w32 codecs, check this site:

[https://answers.launchpad.net/ubuntu/+source/amarok/+question/4378](https://answers.launchpad.net/ubuntu/+source/amarok/+question/4378)

assumes you use amarok, btw

---

### Post by geek2330 on 2007-05-10
I'm using Firefox with Kubuntu, The JRE has been installed from the repository....let me know if I need a different Java plugin.

BTW - since I'm new to Kubuntu and experimenting with this, which one is a good/decent media player, I know there are so many.....but wanted to narrow down my options....

Thanks for the feedback

---

### Post by louieb on 2007-05-11
Was just about to start a new thread asking what is needed to listen to radio stations over the internet  like I can in XP. 
geek2330, hope you don't mind my hitching a ride on this thread but I'd really like to get a radio tuner working.  
  I have Ubuntu Feisty on the laptop and Ubuntu Dapper on the desktop. I use Firefox 2 on both. 
Saw streamtuner mentioned in another thread and geek2330 writes it doesn't work as well as he would like. 
So wondering what else is out there and how happy are you with the way it works.
Thanks, lou.

---

### Post by geek2330 on 2007-05-11
bump.....anyone?

---

### Post by jjross on 2007-05-11
mplayer and mplayer plugin for firefox and w32 codecs should make you able to listen to streaming radio.
It usually works with Gnome and totem out of the box but I've never gotten along with totem so I have always used mplayer.

---

### Post by wmichaelb on 2007-05-11
I had similar problems, but was able to fix them thusly:

[http://ubuntuforums.org/member.php?u=97920](http://ubuntuforums.org/member.php?u=97920)

Check it out!

---

### Post by louieb on 2007-05-11
> **wmichaelb said:**
> Check it out!
Just a little confused here? Link is to your profile.

---

### Post by geek2330 on 2007-05-12
> **louieb said:**
> Just a little confused here? Link is to your profile.

Ditto, that's his profile.....

---

### Post by texasjim on 2007-05-13
> **louieb said:**
> Was just about to start a new thread asking what is needed to listen to radio stations over the internet  like I can in XP. 
geek2330, hope you don't mind my hitching a ride on this thread but I'd really like to get a radio tuner working.  
  I have Ubuntu Feisty on the laptop and Ubuntu Dapper on the desktop. I use Firefox 2 on both. 
Saw streamtuner mentioned in another thread and geek2330 writes it doesn't work as well as he would like. 
So wondering what else is out there and how happy are you with the way it works.
Thanks, lou.

Mine set op pretty easily:
1.Download AUTOMATIX or AUTOMATIX2 for feisty and install.
2. Use it to install all the codecs you legally or morally can.
3. Download and install STREAMTUNER and/or LISTEN.
 
all downloads use synaptic package manager or from automatix, no getting your fingers dirty.
I prefer the LISTEN player in conjunction with FROSTWIRE to download, but am currently having some hang-up 100%CPU opportunities.

---

### Post by louieb on 2007-05-14
> **texasjim said:**
> Mine set op pretty easily:
1.Download AUTOMATIX or AUTOMATIX2 for feisty and install.
2. Use it to install all the codecs you legally or morally can.
3. Download and install STREAMTUNER and/or LISTEN.
 
I was going to try to stay away from automatix, but now I'm going to try it. I'll get back and let you know how it works. Thanks.

---

### Post by compiledkernel on 2007-05-14
sudo apt-get install streamtuner streamripper 


Streamtuner to listen

Streamripper to cut from. I find this useful for talk radio shows that are published over the net. Very helpful.

---

### Post by geek2330 on 2007-05-15
Still having issues with this.

Just installed mplayer and mplayer plugin as suggested, also installed JRE, the first radio station says "Loading Audio....." and stays there for some time, then it is stopped.

Do I have to try streamtuner then ???:confused:

---

### Post by louieb on 2007-05-16
On the PC running Dapper:
Installed codecs, sun java jre thruough AUTOMATIX2
installed streamtuner - ripper through Synaptic.
Streamtuner wanted xmms also so installed it too.
Can now get audio through  Streamtuner.  Havent figured out streamripper yet.
At least Firefox windows look better but no sound yet. 
Fell like I'm making progress. Thanks all.

Going to see what happens  with the laptop running Feisty. Let you know.

---

### Post by louieb on 2007-05-17
Finally got Feisty playing the stream at [http://www.theticket.com/](http://www.theticket.com/) 
the codecs automax mplaayer and this plugin [MediaPlayerConnectivity :: Firefox Add-ons]("https://addons.mozilla.org/en-US/firefox/addon/446")
Now on to the Dapper desktop.

---

### Post by louieb on 2007-05-17
Pretty much the same for Dapper
1.Download AUTOMATIX or AUTOMATIX2 for Dapper and install.
2. Use it to install all the codecs you legally or morally can.
3. Download and install mplayer and Firefox plug in
4. My missing link was the add on   [MediaPlayerConnectivity :: Firefox Add-ons]("https://addons.mozilla.org/en-US/firefox/addon/446")

Can now listen to my favorite radio stations internet stream.

---

### Post by Honayo on 2007-05-17
I agree with louieb. Automatix2 and [this link]("http://desktoplinux.com/articles/AT3648616185.html") solved my problems with streaming audio on a  dual boot Dapper/XP desktop and a Feisty desktop.

Now if I could just check mail on the server as I do in Incredimail, I would be a total convert to Ubuntu / Kubuntu.

---

