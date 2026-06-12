---
title: "Help!!! Setting up a Domain server..."
date: 2005-11-23
forum: Desktop Environments
---

### Post by bfonseca on 2005-11-23
Hi all I am new to linux, but I am very happy with it. I have converted over from windows XP.  I would like to learn all about linux and so I took on a project.  The project is to create a domain server for a website of mine.  The problem is that I dont know where to begin. I have installed Apache from System==>Admin==>Synaptic.  I do not know how to open or configure it. Any help would be greatly appreciated.

I am running Ubuntu 5.10, well i dont know what info you may need so please let me know and I will post it. Thank you for taking the time to help..
Brian

---

### Post by Zelut on 2005-11-23
well if you've installed apache via synaptic it should already be running.  You can see some more tips here [www.ubuntuguide.org](www.ubuntuguide.org).  Also try [http://localhost](http://localhost) .  If you want to add a site copy your .html to the /var/www/ directory..

---

### Post by Joey French on 2005-11-23
Yep, what he said. I use mine for simple stuff, so my knowledge is limited. Here are some useful things that I use to control mine. 

Stop apache- sudo apache2ctl stop
Start apache- sudo apache2ctl start
My apache folder lives in /var/www, (yours does too if you just installed). Say I want to move a folder into it named "pictures" and it lives in my /home folder, here's how to get it there:

sudo mv /home/joey/pictures /var/www

Remember, you need to stop and start apache to work with it. You will have trouble doing anything with it if it's running. You can look at what's going on with your apache by going to "localhost", typing in your IP address, or 127.0.0.1.

If anything looks wrong with these simple tips, somebody let me know. I am not very versed at running servers, but I have been able to host from my box with apache with no trouble for some time, using these simple little pointers. I am sure there are tons of people who can teach you tons of things about apache, but really the best advice is read the docs. They are extensive, to say the least.

---

### Post by bfonseca on 2005-11-23
hi thanks for replying so fast to my problem.  I am also new to using the forums so i didnt expect it to work so fast.  I did what both kuyaedz and joey French said and i guess the problem i have is I can not stop and restart teh apache. Wierd it maybe something  that i am typing.  Both good advice I went to Ubuntuguide.org and that was really helpful too.

Can you please tell me why the stop well not work.

I try :
Stop apache- sudo apache2ctl stop

Error:
sudo: stop: command not found

when I try :
sudo /etc/init.d/apache2 restart

Error:
* Forcing reload of web server (Apache2)...
(98) Address already in use:make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                                           [fail]
Can you help me with the problems i listed up above. I tried what you both said and i got those errors. not sure why. do i have to enable an alias for stop or something of the sort, because it is not being recognized. Thanks again
Brian

---

### Post by bfonseca on 2005-11-24
okay I thank both of you i kepted trying and finally figured out that i was typing it in wrong.  I now got it to work.  Thanks for both your help.
brian

---

### Post by Joey French on 2005-11-26
Sorry, didn't see your reply. Glad you got it straightened out.

---

