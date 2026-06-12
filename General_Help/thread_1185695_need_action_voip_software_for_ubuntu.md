---
title: "need action voip software for ubuntu"
date: 2009-06-12
forum: General Help
---

### Post by shilpiharish on 2009-06-12
hiiiiiiiiiiiiiii all

Can any body please help me to install ACTION VOIP in ubuntu..

if so please gimme the link of download

i will b very thankful to you...


regards
harish

---

### Post by gradinaruvasile on 2009-06-12
Ummm
[http://www.actionvoip.com/en/download.html]("http://www.actionvoip.com/en/download.html")
?
Googling isnt that hard...
It seems that it has linux version too

---

### Post by shilpiharish on 2009-06-12
Dear gradinaruvasile,

i tried with the same link earlier.....
but when i click on that link it will go for rigistration...

when we register our account will get created but there is no option for linux further......

harish

---

### Post by gradinaruvasile on 2009-06-12
I apologize if i offended you. I didnt know you searched for it.
Anyways i couldnt find else either except for some SDK s for linux.

---

### Post by shilpiharish on 2009-06-12
no no thats not a big problem......

i am searching for it.i think i may get some other link...
nyways thanx for ur co operation

---

### Post by Suryaveer on 2009-10-17
Hi. I'm also facing similar problem as u.. I also have loads of balance in my actionVoip client. I have recently moved to Ubuntu 8.04. Not a great deal of experience. I installed wine.I downloaded the '.exe' file on my desktop
Then after going to root and then to my desktop, did
wine setupActionVoip.exe. Thus I was able to install action voip. even the log in screen appeared..
But because of some reason it doesn't allow me to log on.. I also sent the passwrd back to my email accnt and tried copy pasting username and passwrd.. it just doesn't accept.
Did u learn into similar issues..?
Do you know a solution...?

PS: The last time i as using actionVoip on windows, my windows system just crashed, I can't even load it again, so might be that actionVoip still thinks I'm in that session... and doesn't allow me to relogin..
If it is the case.. do you know where the tmp file for this is stored...?
Thanks fr reading. nay suggestions will be helpful!

Suryaveer

---

### Post by mailsub2000 on 2010-02-27
Hi, May be you can try this if possible. I tried as below:
I have amd64 dell vostro 1000. Installed ubuntu 9.10 and ekiga with default option.
Then open ekiga and do basic configuration. Basically decline registering ekiga account. 
Now add action voip account using info as below:
account name: actiovoip
[COLOR=#333333][FONT=Arial]registrar : sip.actionvoip.com[/FONT][/COLOR]
user: <username> [which you get from registration page, you mentioned earlier]
authetication user: <same name above>
password:<password>
timeout:600

and enable account. The account dialog should display the account as registered.
 If you dont see that. try enabling disabling account. If you cant succeed that part
 then we need some experts help.

In my case it worked w/o any special setting.
Hope this helps. Similar is the case with voip raider account.

I am new to linux and search internet even for basic things. So cant help much in details.
 But things above worked well for me. And hope same with you.
cheers

---

### Post by afsal21 on 2010-03-14
yes, ekiga is the best solution.ekiga 2.o or 3.o both  working with action voip as well as smartvoip.

---

### Post by dineshlakshmanan on 2010-05-02
Hi,

     I have followed all your step.I could create the account.After creating account I am not able to call as per the given guidelines from ekiga websites.

I registered Action voip account as how you explained.

Its evrything done as you instructed.

But I am not able to perform call in Ekiga after registering actionvoip account.

Please kindly provide me step by step how to make calls after registering actionvoip account in Ekiga.

Waiting for the reply.

Thanks in Advance!!!!

---

### Post by agkrish on 2010-05-04
Hi mailsub2000 

i hv regd action voip as mentioned in ur post - got the msg could not register (timeout) - so am hvg to use Vista to make calls thru action voip and other voip s/w

is that a typo in ur post actiovoip instead of actionvoip ?

am in the process of upgrading to 10.04LTS - hopefully it works on that

rgs

AMD Turion X2 64 bit ,3 GB RAM,  320 GB HDD
HP Pavilion dv5-1050ee; ATI Radeon
(poor design by HP - serious overheating issues)

---

### Post by dineshlakshmanan on 2010-05-07
> **mailsub2000 said:**
> Hi, May be you can try this if possible. I tried as below:
I have amd64 dell vostro 1000. Installed ubuntu 9.10 and ekiga with default option.
Then open ekiga and do basic configuration. Basically decline registering ekiga account. 
Now add action voip account using info as below:
account name: actiovoip
[COLOR=#333333][FONT=Arial]registrar : sip.actionvoip.com[/FONT][/COLOR]
user: <username> [which you get from registration page, you mentioned earlier]
authetication user: <same name above>
password:<password>
timeout:600

and enable account. The account dialog should display the account as registered.
 If you dont see that. try enabling disabling account. If you cant succeed that part
 then we need some experts help.

In my case it worked w/o any special setting.
Hope this helps. Similar is the case with voip raider account.

I am new to linux and search internet even for basic things. So cant help much in details.
 But things above worked well for me. And hope same with you.
cheers




Hi mailsub2000,

     I have followed all your step.I could create the account.After  creating account I am not able to call as per the given guidelines from  ekiga websites.

I registered Action voip account as how you explained.

Its evrything done as you instructed.

But I am not able to perform call in Ekiga after registering actionvoip  account.

Please kindly provide me step by step how to make calls after  registering actionvoip account in Ekiga.

Waiting for the reply.

Thanks in Advance!!!!

---

### Post by croissont on 2010-05-12
> **mailsub2000 said:**
> Hi, May be you can try this if possible. I tried as below:
I have amd64 dell vostro 1000. Installed ubuntu 9.10 and ekiga with default option.
Then open ekiga and do basic configuration. Basically decline registering ekiga account. 
Now add action voip account using info as below:
account name: actiovoip
[COLOR=#333333][FONT=Arial]registrar : sip.actionvoip.com[/FONT][/COLOR]
user: <username> [which you get from registration page, you mentioned earlier]
authetication user: <same name above>
password:<password>
timeout:600

and enable account. The account dialog should display the account as registered.
 If you dont see that. try enabling disabling account. If you cant succeed that part
 then we need some experts help.

In my case it worked w/o any special setting.
Hope this helps. Similar is the case with voip raider account.

I am new to linux and search internet even for basic things. So cant help much in details.
 But things above worked well for me. And hope same with you.
cheers

I followed your method and it worked perfectly fine. I am using 9.04 on a
Dell Inspiron 6000, so yeah, thanks :D

---

### Post by madhumt on 2011-02-21
> **shilpiharish said:**
> hiiiiiiiiiiiiiii all

Can any body please help me to install ACTION VOIP in ubuntu..

if so please gimme the link of download

i will b very thankful to you...


regards
harish
@ShilpiHarish, 
Hai. I hope by now you might have solved the problem with Action VOIP. if not use Qutecom which is a VOIP application based on SIP protocol. I am using it and it is very easy to configure and use.
Account name   Type anything e. Action VOIP
Login/username      Your actionvoip user id
Password                same as yours
SIP Domain             sip.actionvoip.com
In the server/proxy field also you enter sip.actionvoip.com

Thats it!!!!!!!   Now you can make call as usual as you do in Windows

The same procedure is applicable to all other VOIP services like Jumblo,smartvoip etc...


Bye All the best
MT

---

### Post by sarangbokare on 2012-12-20
> **afsal21 said:**
> yes, ekiga is the best solution. ekiga 2.o or 3.o both  working with action voip as well as smartvoip.


as per below instruction i got register with action voip account but i can not call, even when i try test echo or call back test i am not getting any voice. 

please give me suggestion on same 

Sarang

---

### Post by overdrank on 2012-12-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

