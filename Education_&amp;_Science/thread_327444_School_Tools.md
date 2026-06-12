---
title: "School Tools"
date: 2006-12-29
forum: Education &amp; Science
---

### Post by M8M on 2006-12-29
I'm trying to set up school tools for my family b/c we are a bif home schooling family and that would just make school so much more organized and fun.

Is there someone out there that knows how to use and set up the school tools? Could you walk me through that process/

Thank you,
M8M

---

### Post by slaanco on 2006-12-29
what types of school tools ?

---

### Post by M8M on 2006-12-29
If you go to the following link: [http://www.edubuntu.org/screenshots](http://www.edubuntu.org/screenshots) and scroll about halfway down the page, you will find that it is promoted as part of edubuntu. I can't find the link rihgt now, but I did see a demo for it and it was perfect for our home school setting: coordinating curriculum and calendars. It says on the page I gave you that the tools can be accessed by entering "localhost:7080" into FireFox and I have done so, but it doesn't permit me to access any of the features. I was hoping SOMEONE out there would be able to walk me through it as I can't find any guide or instructions online. What's the point of promoting it, if we can't try it?

Thanks

M8M

---

### Post by slimdog360 on 2006-12-30
what do you mean when it says it wont permit you to use any of its features? Does the page come up but you just cant do anything?

If nothing comes up at all maybe you have a firewall blocking that port. Try turning off the firewall and give it a go.

I know this is a stupid question but youd be suprised at what some people ask, so forgive me for asking this, do you even have edubuntu installed? Or just Ubuntu like it says in your profile thingy.

---

### Post by M8M on 2006-12-30
No problems. I understand the question. Yes, I have recently installed edubuntu on my computer b/c I was wanting to use the school tools.

I have pasted in the local host command, and I do get to the same page they tell me I should be able to get, but I can´t add info. If I go to system > administration > student control panel I have to put my password and it loads a panel that I cannot modify, b/c I must first select a student. However I find no place to input a student.

From what I read earlier, I must create some kind of database that must be hosted on webspace and each student can log in to find their lesson plans, student/teacher communications, etc. I have webspace with my internet provider and I´m hoping that that´s enough, but I´m kinda counting on the info being available to guide me through the setup process....

Has anyone used these features yet? 

Thank you.
M8M

---

### Post by mikeyandmary on 2007-01-01
Have you considered using moodle? Moodle is a web based program that allows you to create online activites for students as well as being able to track performance. I have used this software as a teacher and an spending some of my summer break (I'm in Sydney, Australia) setting up my own moodle server. 

You will need to install LAMP (ubuntu web server) and the moodle software from [www.moodle.org](www.moodle.org)

---

### Post by M8M on 2007-01-03
Thank you for your suggestion. One of the creators of school tools informed me that school tools is still quite unstable, and he too suggested moodle. I just finished looking through the site and I like it alot. The only difficulty is that I am a complete newbie to this whole ubuntu/edubuntu stuff and I still haven´t figured out how to install tgz files. The easiest way for me would be to use automatix or synaptic package management. I have used the terminal too and can work with that if someone else gives me step by step what to do, but I prefer the first two. I imagine that I should be able to add a repository site to synaptic, but I´m not sure which site to use (YET, I´m still looking.)

Could you help me set this up? There are a lot of terms that I don´t know yet and I´m not sure what is the best method to use in my case, etc...

Once I get this all set up, it should take me a LONG way and make life MUCH easier for me!

M8M

---

### Post by oprogue on 2007-01-15
I too am interested in setting up a moodle server.  I'll expidite my efforts by downloading the most current release of edubuntu today.  ... hopefully figure out how to install LAMP and then Moodle itself.  I'll try to document it step by step for future reference.

Please keep me appraised of your progress as well please.

Thanks.

---

### Post by ivanoz on 2007-06-17
hey fellas, well I'm not a geek of using Ubuntu or Moodle, but i can give you a quick guide of how to install moodle in Ubuntu, using Synaptic

Firstly, i have ubuntu feisty, so this guide will be for Feisty.

First you need to install a LAMP server so:

1.- go to System > Administration > Synaptic Packet Manager
2.- click on Edit > mark packages by task
3.- click and mark LAMP Server
4.- click apply

wait till your LAMP server is installed, so you can see if it works by typing localhost in Firefox, if opens a page or something like that, is working

Now, lets install Moodle

1.- go to System > Administration > Synaptic Packet Manager
2.- in search type moodle
3.- click and mark moodle
4.- click apply.
5.- while installing it wiil ask you some questions like:
the name of your server (by default is localhost, unless you have changed it), then your database manager, here you have to chose MySQL and NOT Postrgres), then your DBA name (in MySQL is root, so you have to type root), leave the password blank (by default in MySQL root doesn't have a password), and finally your moodle account and the password for that data base, so type a password if you want.

once all those are done, close Synaptic and open your firefox, type: localhost/moodle and follow the steps, and thats it, moodle will be installed and working in you Ubuntu/Edubuntu.

Hope this helps, i'll try to make a proper installation guide i just need to find some time and i'll do it :D.

cya fellas

---

