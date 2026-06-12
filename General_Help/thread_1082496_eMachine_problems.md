---
title: "eMachine problems"
date: 2009-02-27
forum: General Help
---

### Post by mikemykel on 2009-02-27
About a week ago I posted a problem on another forum and got NO help, so I am going to try again here.

i; I bought a eMachine notebook a couple of weeks ago through Woot and it looks like a fairly decent machine for the price ($300.) It claimed to be ready for Linux with a distro called Linpus installed. I bought it because I have been curious about Linux for quite a while and simply want something I can use to learn on.

However, I cannot get it to boot off the eMachine disc that came with it at all. I get a long scroll of white on black stuff I do not understand with a place for a command prompt at the end. I tried all the different boot options I could find but to no avail. I then tried to use a Ubuntu 8.4 both as live and an install. Either way it boots and finally the screen shows a very distorted image of five Hardy Hurons with a lot of horizontal lines and nothing intelligible.

a. Is the machine itself defective? 
b. Would it help if I stripped the old installation out and if so how do I do that? 
c. I bought a book Ubuntu for Non Geeks 3rd ed. by Rickford Grant and am willing to do my homework -- however?
d. Would anyone like to buy a Notebook eMachine and a fat manual real cheep.

By the way, eMachine Customer Service is very nice but no one there knows anything about Linux. Nothing!

Thanks, Mike Mykel

---

### Post by Girya on 2009-02-27
Try the simple stuff first: boot off the harddisk and when you get to the command prompt type: > startx

if there is a gui it should start. if not type > lspci|less

and use the up and down arrows to scroll thru the output looking for graphics info. then google the graphics card and ubuntu; you'll probably find a way to configure the laptop to run ubuntu.

another option is to try a differnt live cd to see if that one works; puppy linux is one that seems to work on a lot of differdnt machines.

If you are a masochist you can learn the command line. you can do most things on the command line that you do with a gui. There are things you can do with the command line that you can't do with a gui: scripting. 
[http://linuxcommand.org/index.php]("http://linuxcommand.org/index.php")

---

