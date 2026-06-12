---
title: "gmail"
date: 2005-12-07
forum: Desktop Environments
---

### Post by syntaxtothe on 2005-12-07
Yet another one I know -_-

I've searched and searched and to no avail, so here is my problem:

This Ubuntu copy is about 2-3 months old on this box, and I have evolution version 2.4.1

I set up my gmail, properly, as other threads indicated in these forums, and one day my smtp just stops working ! So now I can only receive pop emails, yet I can't email anyone anything, this is outright ridiculous. If anyone knows what it could be pray tell.

---

### Post by carlosqueso on 2005-12-07
I had a similar problem, it may actually be the people that run your smtp server.  Usually you use your ISP's smtp, not your e-mail providers.  If that doesn't fix it, I"m not sure.

---

### Post by shanghaipi on 2005-12-07
I'm using smtp.gmail.com and its working fine.  Initially, I tried sending a message to myself through pop3, and I couldn't receive my own email, but that might be some type of glitch with google.  Otherwise, I can send and receive messages fine.

---

### Post by frost_ad on 2005-12-07
[QUOTE=carlosqueso]I had a similar problem, it may actually be the people that run your smtp server.  Usually you use your ISP's smtp, not your e-mail providers.  If that doesn't fix it, I"m not sure.[/QUOTE]

I agree completely. I was using my email smtp for a long time and one day it just quit. Your ISP may or may not allow using other smtp servers. And even if they have in the past they may have stopped all of a sudden like my ISP did.

---

### Post by cstudent on 2005-12-07
I just use sendmail for smtp.

---

### Post by shanghaipi on 2005-12-07
what's sendmail?

---

### Post by syntaxtothe on 2005-12-07
...all of a sudden, I highly doubt that because my friend has the same version of ubuntu and same ISP, he uses gmail's smtp server fine..... Mine just won't send. 
Yeah so what is sendmail?

---

### Post by shanghaipi on 2005-12-07
do you have one or more email accounts that you are using with evolution.  Maybe something got muddled up between the two.  There is always user error too, i find that most of the problems that i post on this forum happen because I did them and overlooked them in the troubleshooting process because I thought it wouldn't be *that* obvious.

---

### Post by art on 2005-12-07
Which port are you using for gmail? If it's 25 which is default try 465

---

### Post by teaker1s on 2005-12-07
note that gmail servers are now

pop.googlemail.com 995
smtp.googlemail.com 587

login via webpage and you can enable email forwarding and in help section search thunderbird and follow the instructions

---

### Post by syntaxtothe on 2005-12-07
I am not utilising thunderbird mate, I'm using evolution, and as far as I can see there are no ports to configure. Also there really is no room for user error (I'm using one account) and one day it just stopped working.

---

### Post by megamania on 2005-12-07
[QUOTE=shanghaipi]There is always user error too, i find that most of the problems that i post on this forum happen because I did them and overlooked them in the troubleshooting process because I thought it wouldn't be *that* obvious.[/QUOTE]

I understand what you mean here. Not later than two hours ago I went *crazy* trying to "fix" my wireless keyboard which had suddenly stopped working right after rebooting my computer.
The wireless mouse was working perfectly, so I thought it was the batteries. After changing the batteries, it still wouldn't work, so I made a "sync" between the base and the keyboard. Nothing.

After three (3) reboots and five (5) attempts to estabilish a connection between the base and the keyboard, I realized that the cable connecting the base to the computer keyboard plug had fallen on the floor (aaaarghhh).

*Should I go back to Windows? These things do not happen when you have a Windows OS installed* :-)

---

### Post by soulestream on 2005-12-07
Call your ISP. Many ISP's are now blocking access to other companies smtp servers. This is supposed to cut down on spammers. It doesnt,but it is happening.

soule

---

### Post by atoponce on 2005-12-07
[quote=shanghaipi]I'm using smtp.gmail.com and its working fine.  Initially, I tried sending a message to myself through pop3, and I couldn't receive my own email, but that might be some type of glitch with google.  Otherwise, I can send and receive messages fine.[/quote] This is an issue with Evolution, and not GMail.  Evolution has showed problems with sending messages to yourself, for whatever reason.  I think it has something to do with how Evolution handles email headers, but I could be wrong.

---

### Post by adduds on 2005-12-07
[QUOTE=atoponce]This is an issue with Evolution, and not GMail.  Evolution has showed problems with sending messages to yourself, for whatever reason.  I think it has something to do with how Evolution handles email headers, but I could be wrong.[/QUOTE]

I just tried and it sent, althought it does not show up in evolution...:S...but it does send to gmail

---

### Post by atoponce on 2005-12-07
[quote=adduds]I just tried and it sent, althought it does not show up in evolution...:S...but it does send to gmail[/quote] Correct.  That is what I am saying.  Evolution won't show the newly sent email to yourself in the inbox, but GMail will.  Go figure.

However, if you use Thunderbird...

---

### Post by syntaxtothe on 2005-12-07
...evolution was the sexy, but if I must, I'll check out thunderbawd and tell ya'll how it handles.

---

### Post by atoponce on 2005-12-07
[quote=syntaxtothe]...evolution was the sexy, but if I must, I'll check out thunderbawd and tell ya'll how it handles.[/quote] Here's my list why you just can't go wrong with Thunderbird:[LIST=1]
[*]_Extensions_: Just like with Firefox, there are a number of extensions available on download for further enhancing the email experience.  While the list isn't as extensive as Firefox, it seems to be quite complete.
[*]_Themes_: Plenty of themes available.  You can completely customize the way you would like Thunderbird to look.
[*]_Feed Reader_: Yes, an XML feed reader is builtin to the email client to syndicate all the news and blogs you can handle.  All major XML feeds are supported
[*]_Newsreader_: While common in most email clients, the builtin usenet newsreader seems to be the most user friendly that I have encountered.
[*]_Multi-platform_: Not only for Linux, but Windows and Mac as well.[/LIST]

---

### Post by cstudent on 2005-12-07
When I set up Evolution for my Gmail account I used the sendmail option in the mail account send email properties. It sends mail out directly from your computer, not from an external smtp server. It is a function of postfix which is installed by default in Ubuntu. It works well for my needs and I never have to deal with an smtp server being down. As far as sending myself mail to my Gmail account, I can do that, but when I have Evolution check mail again I will end up with the same message in my sent folder twice. On Gmail via the web I see the message in my inbox, but not as a sent message. Your sent mail will remain local with the sendmail method. Which doesn't bother me, but some people may not like that.

---

### Post by syntaxtothe on 2005-12-07
Thunderbird works absolutely fine nce the ports were set, it seems that evolution has a set of default ports, and no way to change them, ah well, Thunderbird will  have to suffice, thanks a bunch pals.

---

### Post by atoponce on 2005-12-08
[quote=syntaxtothe]Thunderbird works absolutely fine nce the ports were set, it seems that evolution has a set of default ports, and no way to change them, ah well, Thunderbird will  have to suffice, thanks a bunch pals.[/quote] Suffice?   I think you'll enjoy Thunderbird much better than Evolution. ;)

---

