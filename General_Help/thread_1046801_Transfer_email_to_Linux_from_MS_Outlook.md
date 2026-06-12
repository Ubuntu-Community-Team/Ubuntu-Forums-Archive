---
title: "Transfer email to Linux from MS Outlook"
date: 2009-01-21
forum: General Help
---

### Post by yknivag on 2009-01-21
I've been around of these fora for some time now and been using Linux on and off for about 5 years or so.

I need a little help though, making the final move of all my day to day (non-gaming) activity to Ubuntu.

There are many threads on here about how to migrate email from Outlook, typically involving migration in Windows to Thunderbird and then copying the directory to Linux.  I have no difficulty in the copying to Linux but - that's easy, the problem I have is getting my email into Thunderbird in the first place.

I've followed many many tutorials, how-tos, threads, suggestions and allsorts, but I've never managed it yet! I've even tried the PST file reading plug-in for Thunderbird.

The email get there, it's just all marked as un-read and HTML formtted email (ie anything with colours, fonts, pictures etc)  is rendered as the HTML-source rather than correctly.

I'm running MS Outlook XP and the latest download of Thunderbird. I've also tried moving my email to Outlook Express and tried importing from there also, the move to M$OE goes ok, but I have the same problem moving into Thunderbird.

This has been the only thing keeping my XP partition for some time now and I'd really like to move completely if at all possible. So any suggestions will be very welcome.

Thanks in advance people! :)

---

### Post by ellgor on 2009-01-22
Hi,

A suggestion, Kmail, it can import from Outlook or many other clients and its unix based, its probabaly got more features than most others and is really easy to work with. Available through the repos (works with Gnome although a KDE app) as a stand alone app or there is a complimentry app, Kontact, which is like a Journal/Diary manager, hope this of help.

Regards, Ellgor.

---

### Post by yknivag on 2009-01-22
Thanks Ellgor, I'll give it a try.

---

### Post by yknivag on 2009-01-23
I can't get kmail to work, the import wizard never seems to be available (always greyed out on the menu).

Took a look at [Outport]("http://outport.sourceforge.net/index.php") but that only does contacts. It exports all the messages (and preserves the formatting) but not in a form that can be imported into any known email program - which seems rather crazy to me!

Anyone have any ideas how I can get the import wizard to work in kmail under Gnome or have any other ideas as to how I can get my email across to Linux?

---

### Post by stchman on 2009-01-23
> **yknivag said:**
> I've been around of these fora for some time now and been using Linux on and off for about 5 years or so.

I need a little help though, making the final move of all my day to day (non-gaming) activity to Ubuntu.

There are many threads on here about how to migrate email from Outlook, typically involving migration in Windows to Thunderbird and then copying the directory to Linux.  I have no difficulty in the copying to Linux but - that's easy, the problem I have is getting my email into Thunderbird in the first place.

I've followed many many tutorials, how-tos, threads, suggestions and allsorts, but I've never managed it yet! I've even tried the PST file reading plug-in for Thunderbird.

The email get there, it's just all marked as un-read and HTML formtted email (ie anything with colours, fonts, pictures etc)  is rendered as the HTML-source rather than correctly.

I'm running MS Outlook XP and the latest download of Thunderbird. I've also tried moving my email to Outlook Express and tried importing from there also, the move to M$OE goes ok, but I have the same problem moving into Thunderbird.

This has been the only thing keeping my XP partition for some time now and I'd really like to move completely if at all possible. So any suggestions will be very welcome.

Thanks in advance people! :)

The easiest way I can think of is to install Thunderbird on your machine that has Outlook.  Then when you initially run Thunderbird it will ask you if you woul like to import mail.  Respond yes and it will import your mail from Outlook into Thunderbird.

Since you said you have no problem transferring the mail once it is in Thunderbird then there you go.

I believe that the import feature of the Ubuntu installer can import email to Evolution.  I believe Evolution and Thunderbird use the same format.

---

### Post by yknivag on 2009-01-23
> **stchman said:**
> The easiest way I can think of is to install Thunderbird on your machine that has Outlook.  Then when you initially run Thunderbird it will ask you if you woul like to import mail.  Respond yes and it will import your mail from Outlook into Thunderbird.

Hi stchman, I'm afraid I've tried the Thunderbird method many many times with no success (details in my first post on this thread).  Do you know away around these issues?

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> Hi stchman, I'm afraid I've tried the Thunderbird method many many times with no success (details in my first post on this thread).  Do you know away around these issues?

One other but more complicated method to use is the following :

1) Set up an imap server on an ubuntu box in your network
2) Have outlook connect to the imap server box
3) Copy your mailboxes to the imap server
4) Boot into linux, and connect thunderbird to the imap server
5) Copy the mailboxes from the imap server to the "local folders" of thunderbird

I've used this method years ago for a colleague with Pegasus [..shiver] Mail, to get it to the imap server and then use Thunderbird.

Of course it depends how many mailboxes you have, a lot of mailboxes make this a lot of work.

---

### Post by albinootje on 2009-01-23
Setting up an imap server for this is really easy on Ubuntu.
```

sudo apt-get install dovecot-imapd

```

After that you might just have to check the line with :
```

protocols = imap imaps

```
in /etc/dovecot/dovecot.conf .. but I think even that is not needed.

To check whether dovecot imap server runs :
```

netstat -ta|grep imap

```

Then run Outlook inside Wine on your Ubuntu, copy your Outlook mailbox structure inside the Wine C: drive, and connect Outlook to the imap server on localhost. Start copying.. etc.

---

### Post by yknivag on 2009-01-23
Hi albinootje, thank you for your reply.

I have installed dovecot-imapd on my other laptop and it's running.
```

:~$ netstat -ta | grep imap
tcp     0     0 *:imaps          *:*
     LISTEN
tcp     0     0 *:imap2          *:*
     LISTEN
:~$

```
However when I try and connect without SSL I get an auth error, when I connect with SSL I get warnings about the certificate not being trusted but if I say to trust it anyway Outlook disconnects straight away.

Do I need to set up an IMAP user in dovecot before I connect? Or does it automatically assume my Ubuntu login?

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> 
Do I need to set up an IMAP user in dovecot before I connect? Or does it automatically assume my Ubuntu login?

Good that you have it running.
Dovecot will work with your Ubuntu username by default.

Let's see whether Outlook wants to work at all with a hand made SSL cert.

---

### Post by albinootje on 2009-01-23
Are you using Outlook or Outlook Express ? And what version ?

Just came across this :
[http://www.linuxquestions.org/questions/linux-enterprise-47/dovecot-and-outlook-613467/](http://www.linuxquestions.org/questions/linux-enterprise-47/dovecot-and-outlook-613467/)
> 
Outlook is terrible for IMAP. You would be surprised to know that Outlook Express works very well with IMAP but not regular Outlook. I guess Outlook was designed mostly for use with Exchange.


---

### Post by yknivag on 2009-01-23
I'm using Outlook XP, I'll try setting up Outlook Express (as I can easily move my mail to OE from Outlook).

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> I'm using Outlook XP, I'll try setting up Outlook Express (as I can easily move my mail to OE from Outlook).

Cool. I'm curious about the end result.

---

### Post by yknivag on 2009-01-23
Getting slightly further but still not able to connect.

```

Configuration:
   Account: 10.0.0.3
   Server: 10.0.0.3
   User name: gavin
   Protocol: IMAP
   Port: 143
   Secure(SSL): 0
   Code: 800ccc0f

```
then
```

Your IMAP server wishes to alert you to the following: Cannot connect to IMAP server 10.0.0.3 (10.0.0.3:143), connect error 10061

```
I've never used IMAP and am completely confused now... :(

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> Getting slightly further but still not able to connect.

```

Configuration:
   Account: 10.0.0.3
   Server: 10.0.0.3
   User name: gavin
   Protocol: IMAP
   Port: 143
   Secure(SSL): 0
   Code: 800ccc0f

```
then
```

Your IMAP server wishes to alert you to the following: Cannot connect to IMAP server 10.0.0.3 (10.0.0.3:143), connect error 10061

```
I've never used IMAP and am completely confused now... :(

I have never used Outlook or Outlook Express, but Dovecot imap server is running on 0.0.0.0 which means that either 127.0.0.1 or your own ip address should be OK, and the rest looks good.

Do you have a firewall enabled on your Ubuntu box ?
Then 127.0.0.1 or 127.0.1.1 would make more sense to use.

---

### Post by albinootje on 2009-01-23
And can you make sure, with for example Thunderbird or Evolution, that you can connect correctly to the Dovecot imap server ?
Just in case.

---

### Post by yknivag on 2009-01-23
OK, I can connect to the IMAP server in Outlook Express but not Outlook.  However, when I import my messages into Outlook Express I lose the HTML/formatting (as per my original post) :'(

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> OK, I can connect to the IMAP server in Outlook Express but not Outlook.  However, when I import my messages into Outlook Express I lose the HTML/formatting (as per my original post) :'(

Sorry to hear that :(

Can you try this software : 
[http://www.aid4mail.com/?af=p_emailman](http://www.aid4mail.com/?af=p_emailman)
I'm not sure how restricted the trial version is, but I heard that it is good.

---

### Post by yknivag on 2009-01-23
WooHoo!!

This is looking very very promising albinootje! :)

I am connected from Outlook and can copy mails into the IMAP folders and then I can see them in Outlook preserving the formatting.

Just need to get a Linux client to connect to the IMAP now...

Thank you so much for your help so far.

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
>  I am connected from Outlook and can copy mails into the IMAP folders and then I can see them in Outlook preserving the formatting.


Great!
I was just reading this :
[http://www.labnol.org/internet/email/export-outlook-email-to-gmail-pst-backup/1938/](http://www.labnol.org/internet/email/export-outlook-email-to-gmail-pst-backup/1938/)

.. And got confused because there people have Outlook (and Outlook Express) working with Gmail's imap server, while others were writing that Outlook was working not well with imap :)

---

### Post by yknivag on 2009-01-23
Albinootje, you are a genius!!!

:):):)

I have never been this close to getting the transfer to work!

Having problems with some mail not preserving state correctly, but some is which is far more promising than I've ever seen before.

Will need some verification that I can live with the current level of corruption (presumably caused by Outlook's poor MIME type recognition) but this is surely looking very positive.

You may be single handedly responsible for my finally getting out of Windoze.

Thank you for all your help!

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> 
You may be single handedly responsible for my finally getting out of Windoze.

You made my day! :)
> 
Thank you for all your help!
You're welcome!

---

### Post by yknivag on 2009-01-23
Nope, still not working.  Everything is visible in Outlook on the IMAP folders, but all ther attachments are missing in Thunderbird, Evolution or Outlook Express.

:(

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> Nope, still not working.  Everything is visible in Outlook on the IMAP folders, but all ther attachments are missing in Thunderbird, Evolution or Outlook Express.

:(

Ouch :(
I've looked through all kind of mail converter software, and some of it is pretty old.
There's also more commercial converters.
I also looked at the FAQ of the commercial mail converter I mentioned earlier in this thread, Outlook is mentioned several times, perhaps useful to read a bit of that.
The 1 pc license is about 50 euros, which could be worth it (after the conversion you can put it on ebay), since I assume you spend your money on MS-Vista yet :| :)

---

### Post by yknivag on 2009-01-23
I've been searching around for about 3 years trying to do this now. :(

I think the only way left is to run Outlook under Wine with my old email and use a Linux client for new mail from now onwards.  Was hoping for a seamless transition.

There are a few commercial programs but I'm not convinced that, if I can't successfully transfer M$ Outlook to M$ OE, they can arrange any better conversion.

---

### Post by albinootje on 2009-01-23
> **yknivag said:**
> I've been searching around for about 3 years trying to do this now. :(

I think the only way left is to run Outlook under Wine with my old email and use a Linux client for new mail from now onwards.  Was hoping for a seamless transition.
> 
If you would know someone who runs a MS-Exchange server it must be possible to get this fixed.
Or maybe with an Exchange alternative like Zarafa it could be possible to do the conversion.


There are a few commercial programs but I'm not convinced that, if I can't successfully transfer M$ Outlook to M$ OE, they can arrange any better conversion.

You might be right about that, but why not test the trial version of those commercial converters ?

And what about "syncing" ?  Is that perhaps what you would need to convert from Outlook to Outlook Express to make the attachments convert too ?
Just wondering.

It reminds me of all those C: drive and E: drive references (for attachments) in the Pegasus Mail emails that I had to convert, pretty annoying :(

---

### Post by yknivag on 2009-01-24
> **albinootje said:**
> It reminds me of all those C: drive and E: drive references (for attachments) in the Pegasus Mail emails that I had to convert, pretty annoying :(

Such nostalgia! I loved Pegasus! Such a wonderfully simple email program. I used it for years. Shame there isn't a Linux version really!

As for my own problem, I think (if it will work) I will run Outlook in WINE or on a virtual machine simply for my "legacy" email and have a fresh start.

Although all this has proved enormously fruitful as you have introduced me to the world of IMAP which may yet solve many problems I have accessing the same email in many places. I am greatly indebted to you.

---

### Post by mvip on 2009-02-03
Just thinking outside the box here a little bit. I don't know how you're getting your emails into Outlook, but if you're using IMAP then this might work for you.

[LIST=1]
[*]Set up a Gmail account
[*]Use an online transfer tool (like [YippieMove]("http://www.yippiemove.com")) and set up the source account to wherever you're getting your emails from in Outlook and the destination to be the Gmail account you just created.
[*]Configure Thunderbird to access Gmail via IMAP.
[/LIST]

Maybe not exactly what you're looking for, but thought I'd put it out the.

---

### Post by yknivag on 2009-02-04
Hi mvip, thanks for your reply. If I were using IMAP I could simply point Thunderbird/Evolution at my IMAP server and all would be sunshine.

Sadly I use POP in Outlook and the messages are stored locally in a .PST file.  Hence I need to keep a Windoze partition or at least get Outlook running in wine or a VM.

Darned M$!

---

### Post by mvip on 2009-02-08
> **yknivag said:**
> Hi mvip, thanks for your reply. If I were using IMAP I could simply point Thunderbird/Evolution at my IMAP server and all would be sunshine.

Sadly I use POP in Outlook and the messages are stored locally in a .PST file.  Hence I need to keep a Windoze partition or at least get Outlook running in wine or a VM.

Darned M$!

Valid point.

Here's another idea tho. Try to find a PST to Mbox conversion tool. Once you've successfully converted the PST to an Mbox, it will be piece a cake to get it into any email client.

---

### Post by HermanAB on 2009-02-08
Hmm, as you are no doubt by now realizing, the best way to transfer Outlook email to Linux is not to bother...

First, install your new Linux mail system and start using it for all new mail.

For the old mail, install Office 2003 or 2007 on Wine or Crossover and copy the PST file to the wine bottle.  Within 3 months or so, you won't use outlook on the old mail anymore.

Cheers,

Herman

---

### Post by yknivag on 2009-02-08
> **mvip said:**
> Valid point.

Here's another idea tho. Try to find a PST to Mbox conversion tool. Once you've successfully converted the PST to an Mbox, it will be piece a cake to get it into any email client.

That's my problem, the converstion tools are not converting correctly.  Messages are either all marked as "unread" or lose all formatting and/or attachments.

---

### Post by nelsondovale on 2009-02-20
Have you tried readpst? it worked pretty fine im my job.

install it with

```
sudo apt-get install readpst
```

then navigate in terminal to the directory where you have your pst file

```
cd directory
```

then run it

```
readpst name.pst
```

finally, copy the output to the proper .evolution directory

---

### Post by karlv on 2009-02-26
Ok. I had the same problem, about 4 GB of Outlook mails in a lot of subfolders. I solved it like this : 

Install Courier on another PC running ubuntu: 
[install guide]("https://help.ubuntu.com/community/Courier")
(very easy + you don't need courier-imap-ssl)

Boot Windows:
Setup the imap server in Outlook 2003. Rightclick on your normal Inbox and select copy. As target use the created IMAP server.
!Be aware that the subfolders don't contain any "." or "/" as it not allowed in IMAP standard and the copy process will not be completed!

Boot Linux: 
Start Evolution. Setup IMAP server and copy back the Folders.

You can now deinstall the IMAP server as it is not needed anymore.

For Calender and Contacts I used: [Outpod]("http://www.stoer.de/ipod/ipod_en.htm")

Start Outpod. Select all youts contacts, right-click. Save selected in one file. This creates a .vcf file. Then import the vcf in Evolution. Same for Calender.

If you don't have a second pc standing around: Install the Courier-IMAP server on your target linux and install Windows+Outlook in a VM. 
A second alternative is to use another Windows-PC and a install the IMAP server on your target linux. 

I hope this helps some of you
karlv

---

