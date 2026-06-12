---
title: "I want to test how secure my network is"
date: 2006-01-09
forum: Desktop Environments
---

### Post by MikieEars on 2006-01-09
If anyone can point me in the right direction or programs to use and such. To test how secure my wireless connection is.

I've read a bunch of articles on WEP cracking, and would like to learn more on this subject regarding my own network. Also it seems to be able to use most of these programs you must collect wireless packets. My problem being, I have no idea how to set my Belkin 7010 notebook card into monitor mode. 

Wep cracking is just one subject. I would also like to know how to find out if I have any open ports and if there is any way people will be able to gain access.

If you could post articles, or even give me a littl;e tutorial that would be great.

If this kind of post doesn't belong here you can delete it oir I will be happy to delete it. 

I know Ubuntu is good about security, or so I've heard. And I want to take full advantage of this.

Thank you

---

### Post by Randomskk on 2006-01-09
If you want to check for open ports, download nmap:
```

sudo apt-get install nmap

``` 
should do the trick.
This is a pretty good program for checking open ports and the likes, while not as fast as scanrand I find it's easier to use and can do more. (Oh, and scanrand doesn't work for me on this machine anyway, so :-P ).

One limitation is that it can only scan other machines, not your own (in my experience, at least) so unless you have another computer you can't use nmap on your own pc.

There are other things as well - Nessus (again, sudo apt-get install nessus nessus-client) is a scanner which can scan your entire network and look for vunerabilities, and makes a nice report when it's done about what services were open, things like that, and sometimes a reccomendation about what to do about the problem.

I'm afraid I can't help you too much on wireless security (my computer doesn't use a wireless connection, I just set it up for my father and my DS :) ) but I can say a few things about securing it (although yeah, I'm no expert..)
WEP keys are good, but pretty easily cracked - as you said, all one needs to do is collect enough packets to crack the key, and then the person's in.
WPA-PSK is probably slightly stronger (it's where all the machines connecting share a key (you have to take the key to each machine, it's like a password) and then they use that; however if someone can geuss the password (or brute force it) they're in again...), but most people find WEP easier / better. 
As well as that, you might want to look into MAC allow lists - you get the MAC address of all computers who will connect to the wireless, and on the wireless router's config page you say only those computers can connect. This adds another level of security, although people can fake MAC addresses.
Finally, disabling DHCP (if you can give all the computers on your network a static IP) is another slight layer of security, as people connecting are not automatically given DNS servers and IP addresses, although this doesn't really stop a determined attacker.

Take what I've said with a pinch of salt, as I said I'm no expert here and what I've learnt is mainly from experimentation. 

This post should probably belong in Security Talk down below a bit, by the way.

PS: as far as using nmap and nessus goes, both need sudo to run well.
Just typing nmap should give you a list of commands you can use, but a normal scan may look something like this:
```

sudo nmap -sV -v -TAggressive -oN scan.log 192.168.0.1

```
That will run a scan that will also try to check versions of running apps (useful if you don't know what's running on a port), will give a little more info than normal (-v), will do the whole scan a little faster than normal (speed isn't so much a concern if you use it on your own computers, where faster is usually better), save the log to scan.log (in the current directory) and, finally, is actually going to scan 192.168.0.1

Nessus is a little more complex, as it's a server-client thing, but basically you need to add a user (sudo nessus-adduser), then run nessus (sudo nessus), then in a different shell run the nessus-client (sudo nessus-client), enter your user details there and login, set the scan (it's a GUI and pretty easy to setup) then start scanning and wait. When it's done you get a report window that you can save, it organises scans by network (top left box), host (bottom left box) and then you see the results on the right side. 

If you've got any questions like this feel free to ask, although I can't promise to know the answer :-P

---

### Post by ranf on 2006-01-09
[QUOTE=MikieEars]If anyone can point me in the right direction or programs to use and such. To test how secure my wireless connection is.

I've read a bunch of articles on WEP cracking, and would like to learn more on this subject regarding my own network. Also it seems to be able to use most of these programs you must collect wireless packets. My problem being, I have no idea how to set my Belkin 7010 notebook card into monitor mode. 
[/QUOTE]
Here is a nice video (Cracking WEP in 10 Minutes):
[http://iwhax.net/index.php/Demos](http://iwhax.net/index.php/Demos)

These guys also have penetration testing live CD. I never tried it though.

I don't know this card. If you're using ndiswrapper then there is no way (AFAIK).

---

### Post by anthro398 on 2006-01-09
I'd use Kismet to find networks, capture packets, and identify clients.  Then I'd put airsnort to work to crack the wep key, though there may be some faster apps for that these days.  I'd leave my access point open for neighbors to use.  I mean, you could always use ssh -d/socks5 proxy to encrypt your data to a machine on the wired network so that your data is flying around unencrypted to be sniffed.

---

### Post by Olav on 2006-01-09
[http://www.nessus.org/](http://www.nessus.org/)

---

### Post by Randomskk on 2006-01-09
[QUOTE=Olav][http://www.nessus.org/](http://www.nessus.org/)[/QUOTE]
Don't need to go there to download it - as I said in my post above,
sudo apt-get install nessus nessus-client
does everything you need.

Unless you want more usage guides, but it's pretty simple.

---

### Post by Olav on 2006-01-09
[QUOTE=Randomskk]Don't need to go there to download it - as I said in my post above,
sudo apt-get install nessus nessus-client
does everything you need.[/QUOTE]
As far as I know there is no **nessus-client** in Breezy. There is, however, **nessus** and **nessusd**. Those are version 2.2.4-2 while on the Nessus site you can get 2.2.6 (or 3.0.1 if you don't mind the commercial license).

> Unless you want more usage guides, but it's pretty simple.
I beg to differ. Anyone who wants to be effective with such a tool, needs to read.

---

### Post by Randomskk on 2006-01-09
Yeah, it's nessus and nessusd, my bad. Weird, I swear there was a -client. oops.

As far as effectivness I'd say he could get a basic idea of his network (I'm assuming it's a fairly small home network, probably only a few hosts) without needing much reading; enough to test for open ports and what could be done with them at any rate.
And I'd still say that installing from apt-get is going to be a lot easier than downloading and installing the latest version from the nessus website, and although I can't speak with experience (I used apt-get, it works fine for me), I've found it's easier to use apt than download and install.. much less chance of errors, too.

Still, like I said, I'm no expert at this. Just trying to help out :)

---

### Post by Olav on 2006-01-09
[QUOTE=Randomskk]Still, like I said, I'm no expert at this. Just trying to help out :)[/QUOTE]
Me too ;) 

Anyway, I don't think installing from source is too difficult, even for a newbie, just make sure you have gcc and make installed. Uncompress the source code, read the INSTALL or README file, or any other instructions that are almost certainly included. Most of the time it's just three commands:
```
./configure
make
make install
```
(as root, of course)

Can't make lots of mistakes with that.

If you want to be able to uninstall or upgrade, install checkinstall with apt-get or Synaptic and then
```
./configure
make
checkinstall
```

A package will be made and installed, that you can later uninstall from Synaptic.

Really, it pays to know a few tricks on the command line :p

---

### Post by blu.gecko on 2006-01-09
check out insecure.org

---

### Post by soulestream on 2006-01-09
> how to find out if I have any open ports and if there is any way people will be able to gain access.

[http://www.grc.com/default.htm](http://www.grc.com/default.htm)

take the sheilds up test

soule

---

### Post by Randomskk on 2006-01-09
[QUOTE=Olav]Me too ;) 

Anyway, I don't think installing from source is too difficult, even for a newbie, just make sure you have gcc and make installed. Uncompress the source code, read the INSTALL or README file, or any other instructions that are almost certainly included. Most of the time it's just three commands:
```
./configure
make
make install
```
(as root, of course)

Can't make lots of mistakes with that.

If you want to be able to uninstall or upgrade, install checkinstall with apt-get or Synaptic and then
```
./configure
make
checkinstall
```

A package will be made and installed, that you can later uninstall from Synaptic.

Really, it pays to know a few tricks on the command line :p[/QUOTE]

I know, but I've had more problems compiling from source than I have with apt-get.
Missing libs, dependencies, broken files, stuff like that tend to make compiling error-prone, while apt will happily download and install everything you need :)

---

### Post by blu.gecko on 2006-01-10
ofcourse you have ports open, do a port test to see what is open, unless you are not browsing the web 53 will be open, most hackers look for 53. I dont hack anymore, but most of those security testing websites are a crock. browse forums and find a licensed ceh and ask him to test out your box. wifi on passwords, the hardest number or key to clone is a spacebar key stoke, so if you are going to password it use psk2 not wep and use passwords like "2T3% 97&hD *45" it will take too long for someone to scan that, and if your box is up to date on security, he or she will more than likely give up.

blu

---

