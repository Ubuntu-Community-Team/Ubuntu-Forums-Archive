---
title: "[SOLVED] Ubuntu Help"
date: 2009-01-07
forum: General Help
---

### Post by krnekhelesh on 2009-01-07
Hi, I did something incredibly stupid and right now I'm in a deep trouble.

First let me tell you what I did.....
I wanted to install skype on my desktop, which I did but since the mic wasnt working, I googled and found a solution in the link I've mentioned below.
[http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/]("http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/")

However in the process of doing what the blog instructed, it also removed my ubuntu-desktop package. At that time I didnt know what package it meant, but after restarting I cannot see the graphical login but the text based command black screen..

So I tried installing the ubuntu-desktop again using the command
***sudo apt-get install ubuntu-desktop***

However it displays a series of error messages which displays that it cannot access the ubuntu website to download the package. I'm in a fix. .what should I do??? I think my sources.list file is corrupt or there are some duplicate entries in it.....

If the only solution is reinstall ubuntu, please mention a way where I can transfer all my data present in the ext3 drive to an external drive. I was using a dual boot system, so I have vista installed in the system too.

Please help....as all my data are in the ext3 drivers....

---

### Post by phisher1 on 2009-01-07
Are you able to access the internet at all?

ping google.com
ping 72.14.205.100

If sources.list is corrupted for some reason, or if you for some reason can't access the internet, you can try using your Ubuntu CD as software repo.

uncomment and/or add this line to /etc/apt/sources.list  .. all on one line.

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

---

### Post by hwttdz on 2009-01-07
Were your home and root on the same partition?

Options to move data:
you should be able to tar it and burn to a cd from the command prompt, I don't know how to burn a cd from command prompt.
there are windows programs for moving data from ext3 partitions, I believe partition magic is the name of one.  
scp it to another computer on the network (if you can connect to another machine on the network). 

Check connectivity of the ubuntu system, it's possible your sources.lst is fine and it's just not connecting properly.
Try ifconfig and see what your output is.
Also try pinging a site and see if it can get the ip address, if it can't try adding the ip address of whatever it needs to connect to to get packages to your hosts file.  

If I had just installed and hadn't made many changes I'd just grab the data and reinstall.  If you have separate home and root partitions this is easy, because you can just leave the home partition alone, and redo the root.  If you don't you're going to need to move your data off.

---

### Post by krnekhelesh on 2009-01-07
I'm sure internet is enabled because, when I tried ***sudo apt-get upgrade***, it says 29.2 MB updates to be installed do you want to proceed? [Y/n], but when I input ***y***,  the same error I mentioned above is displayed, so I guess my source file is corrupt..

---

### Post by phisher1 on 2009-01-07
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

eb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

That should get you all you need if sources.list is corrupted.. I don't see why or why sources.list would be corrupted though.

---

### Post by krnekhelesh on 2009-01-07
wait, what should I do with the links you gave? How do I install ubuntu-desktop?

---

### Post by phisher1 on 2009-01-07
You said you thought your sources.list may be corrupted.

Those lines go in sources.list

...

---

### Post by krnekhelesh on 2009-01-07
so in the text mode, I do gedit /etc/apt/sources.list and then remove whatever is in it, and type the links you gave???

---

### Post by hotstovejer on 2009-01-07
It's ok! Don't panic! We're here to help!

First off, what error message are you getting exactly when you type ```
sudo apt-get upgrade
```

Second, could you post your sources.list? If not, you can ask for a copy so you can download it.

I just broke apt with me trying to install the ubuntu-restricted-extras in my virtual machine, but it's fixable. IT'S ALL FIXABLE! 

Let us know what's up!

Jeremy

---

### Post by phisher1 on 2009-01-07
First of all, I'd like to know why you think your sources.list is corrupt. 

If you weren't even sure what those lines were, I'm doubting you know what sources.list should look like..

I see no reason sources.list would have become corrupted.

There may be other problems going on that we are both not aware of.

---

### Post by hotstovejer on 2009-01-07
> **krnekhelesh said:**
> so in the text mode, I do gedit /etc/apt/sources.list and then remove whatever is in it, and type the links you gave???

You would use nano instead of gedit. So just replace gedit with nano.

Also, to edit sources.list, you need to use sudo, so it would be 

```
sudo nano /etc/apt/sources.list
```

Jeremy

---

### Post by bullium on 2009-01-07
This may help you get back on your feet. [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) This site has some really useful information in regards to Ubuntu specific so you may want to bookmark it.

---

### Post by krnekhelesh on 2009-01-07
I'm posting the output of sudo apt-get upgrade
[I][B]
reading package lists....done
building dependancy tree....done
reading state information....done

The following packages will be upgraded
samba-common  libopal-2.3   thunderbird

11 upgraded, 0  to remove
Need to get 29.2 MB of archives
Do you want to continue [Y/n] 
[/B][/I]
Upon entering yes
[I][B]
Err [http://security.ubuntu.com/intrepid-security/main/samba-common2:3.2.3ubuntu3.4](http://security.ubuntu.com/intrepid-security/main/samba-common2:3.2.3ubuntu3.4)
Could not resolve `security.ubuntu.com`

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient-3.2-ubuntu3.4-i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient-3.2-ubuntu3.4-i386.deb)
Could not resolve `security.ubuntu.com`

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/B][/I]

---

### Post by krnekhelesh on 2009-01-07
Since I was in a text-based environment, I had to copy the output manually in a notebook and then reproduce it back in this post. That's why it took time.

---

### Post by phisher1 on 2009-01-07
Do you have valid nameservers in /etc/resolv.conf ?

If not, try 

sudo echo "nameserver 4.2.2.2" > /etc/resolv.conf

and try your upgrade again

---

### Post by krnekhelesh on 2009-01-07
Since I have been using ubuntu 8.10 for a month now, I've been tweaking around a bit. And many a times I've been asked in many blogs to add 2-3 lines in the sources.list file.

So I assumed that I may have tampered with that file unnecessarily and made it corrupt due to error messages.

---

### Post by krnekhelesh on 2009-01-07
> **bullium said:**
> This may help you get back on your feet. [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) This site has some really useful information in regards to Ubuntu specific so you may want to bookmark it.


At present,  I do not have the ubuntu installation cd with me, but once I get it in 2-3 days, I will try doing what the site mentions.

---

### Post by krnekhelesh on 2009-01-07
> **phisher1 said:**
> Do you have valid nameservers in /etc/resolv.conf ?

If not, try 

sudo echo "nameserver 4.2.2.2" > /etc/resolv.conf

and try your upgrade again

I tried doing this...at first it said you do not have the permissions but I thought I used sudo...

so I logged in as root using su root and then tried the command.
After which I tried sudo apt-get upgrade and I get the same issue.

---

### Post by phisher1 on 2009-01-07
Then you are most likely not online.

ping google.com
ping 72.14.205.100

Do either of those result in replies?

---

### Post by krnekhelesh on 2009-01-07
In this case, I'll try installing from ubuntu-desktop from the CD. thanks for your help....I'll post again if I face any problems further...

---

### Post by Slim Odds on 2009-01-07
> **phisher1 said:**
> 
sudo echo "nameserver 4.2.2.2" > /etc/resolv.conf


Where the heck did you get that IP address?

---

### Post by phisher1 on 2009-01-07
It's one of Level3's open recursive nameservers... Been using it for years..
4.2.2.1 through 4.2.2.6

Easy to remember =)

---

### Post by krnekhelesh on 2009-01-10
ok, I tried everything but still I cant fix the problem.....I tried the following command
***sudo apt-cdrom add***

But when I run ***sudo aptitude install ubuntu-desktop*** it still looks for the package online and I get the error message as before " Could not resolve security.ubuntu.com"

What should I do?

Anyway I kinda messed up the sound drivers, so I would like to do a clean reinstall of ubuntu however my data is still present and I need to back it up. Since I have a dual-boot of vista, could you also mention how I can access my linux files and back it up from vista?

---

### Post by phisher1 on 2009-01-10
Well, at this point I would have to recommend a re-install. For some reason you appear to not be online either. I would recommend popping in a USB drive and backing up your information. A new USB drive should show up as /dev/sdx1  x being a,b,c,d . in order of the number of drives you have in your machine.. If you only have 1 harddrive, it should show up as /dev/sdb1

Then you can sudo mkdir /mnt/usb ; sudo chown yourusername /mnt/usb; sudo mount /dev/sdb1 /mnt/usb 

then copy your files over to /mnt/usb

give that a shot..

---

### Post by krnekhelesh on 2009-01-10
I'll do that...

---

### Post by krnekhelesh on 2009-01-10
all the mounting went fine but while copying the files I faced a problem....I used the command 
***cp /home/nik/Documents/* /mnt/usb***
but while copying this is the output
**cp: omitting directory /home/nik/Documents/folder1**

why is that?

---

### Post by krnekhelesh on 2009-01-10
I solved it.....I just had to add cp -R

---

### Post by krnekhelesh on 2009-01-11
Thanks everyone for your help.....I  reinstalled ubuntu after backing up all my files. Everything is back to normal.....

---

### Post by phisher1 on 2009-01-11
> **krnekhelesh said:**
> Thanks everyone for your help.....I  reinstalled ubuntu after backing up all my files. Everything is back to normal.....

Ahh good to hear.. I was expecting massive failure and tears. :redface:

---

