---
title: "Running as Root"
date: 2009-01-30
forum: Forum Feedback &amp; Help
---

### Post by sweetnessAndLight on 2009-01-30
I would like to respectfully express my extreme disappointment with the attitude toward running as root shown by the recent announcement "New forum policy on log-in-as-root tutorials", in this forum.

I have been told, frequently and with vehemence, that Linux is about CHOICE.  Apparently, Ubuntu forums have decided to opt out of that philosophy.

I guess Ubuntu is about choice, as long as you make the Ubuntu-approved choice.

---

### Post by hyper_ch on 2009-01-30
that anouncement is not recent.

And if you read the anouncment you would understand it. There are only very few things that require an enabled root account. Canonical has chosen to use the sudo path instead. So, if you don't do any very specific things then there is no need for root. If you do very specific things then you should be knowledgable enough about it to activate root.

And with regard to choice: Nobody hinders you to enable your root and do whathever you want with it as root. However you have agreed to respect these forum rules here.

---

### Post by cariboo on 2009-01-30
The way I look at is, that if you have to ask here, then you aren't ready to run as root. A quick search of google will net you more results on how to enable the root account, then you really need.

Jim

---

### Post by snowpine on 2009-01-30
Hi there, it looks like you joined the forums just to tell us that?? (It shows up as your only post.) 

Spend some time here, get to know what the forums are all about. I think you are judging us too quickly. :)

---

### Post by sub2007 on 2009-01-30
This is nothing to do with choice. Ubuntu comes with sudo and does nothing to block you enabling a root account on your own box. All the announcement does is encourage the people you are helping to use sudo rather than su. This is good for a number of reasons:

1. if you are only executing single commands as root then there is a reduced danger in accidentally doing the wrong thing.

2. if inexperienced users realise that they can log in as root then there would be tendancy to do that all the time. Yes that is their choice but choice should be coupled with being well informed. People who don't have the experience of how powerful a root account is can easily bork their install by entering a command incorrectly (a number of people have borked their installs by sudoing a command that they didn't know) or even by deleting a file that you aren't meant to delete.

---

### Post by jenkinbr on 2009-01-30
> **snowpine said:**
> Hi there, it looks like you joined the forums just to tell us that?? (It shows up as your only post.) 

Spend some time here, get to know what the forums are all about. I think you are judging us too quickly. :)
In response to this, many users browse the forums quite a bit before they actually register.  I created my account in November 2007, but I was browsing the forums and getting awnswers to questions for about 6 months before then.

I agree with the statement that if you don't know how to enable root, you probably shouldn't run as root.

---

### Post by sweetnessAndLight on 2009-01-31
Yes, while the start of this thread was my first post, I have been around, usually looking for technical info.

Thank you all for your kind replies.  I do know how to login as root, and yes, there are plenty of places to find out how to do it, though I figured it out on my own.

I had not seen that announcement until the day I posted, and, when I saw it, I was struck by its rather heavy-handed tone, and it reminded me of a phrase from my childhood: "This is for your own good."

Well, 'nuff said.
Thank you all again.

---

### Post by mister_pink on 2009-02-03
Whenever someone asks this they're usually given the official "you don't need root, you can do almost everything with sudo" line. 

Just out of pure curiousity, what can't you do with sudo? I'd count myself as a relatively experienced user, and I can't think of anything that would need you to activate the root account.

---

### Post by jenkinbr on 2009-02-03
*runs to google*

Hmmm, google isn't helping much, other then tell me how to enable and disable root.

---

### Post by p_quarles on 2009-02-03
> **mister_pink said:**
> Whenever someone asks this they're usually given the official "you don't need root, you can do almost everything with sudo" line. 

Just out of pure curiousity, what can't you do with sudo? I'd count myself as a relatively experienced user, and I can't think of anything that would need you to activate the root account.
Certain web-based applications are designed to escalate privileges using the more traditional "su" command, and don't know about sudo. Webmin springs to mind.

In any event, this thread is indicative of a common misapprehension. Root isn't "disabled" in Ubuntu, nor are you prevented from "running as root," or even logging into a root shell. The truth is pretty simple: Ubuntu uses sudo and its graphical front-ends for *authenticating* the root user, rather than the more traditional (and, ultimately, less flexible) su command, or the login shell. None of this limits the administrative user's access to root privileges in any way.

My understanding of the policy is that it forbids two specific things:
1) Suggesting that people set a root password. This goes against the model supported by Ubuntu's developers, and as this is an official support forum, it ought not second-guess the developers.
2) Tutorials/how-tos on enabling graphical root logins. Running your entire X session as root is just a bad idea, but lots of people seem to not realize this. 

But again: nothing in the Ubuntu authentication model in any way restricts the administrative user's privileges. At all.

---

### Post by jenkinbr on 2009-02-03
> **p_quarles said:**
> Certain web-based applications are designed to escalate privileges using the more traditional "su" command, and don't know about sudo. Webmin springs to mind.

In any event, this thread is indicative of a common misapprehension. Root isn't "disabled" in Ubuntu, nor are you prevented from "running as root," or even logging into a root shell. The truth is pretty simple: Ubuntu uses sudo and its graphical front-ends for *authenticating* the root user, rather than the more traditional (and, ultimately, less flexible) su command, or the login shell. None of this limits the administrative user's access to root privileges in any way.

My understanding of the policy is that it forbids two specific things:
1) Suggesting that people set a root password. This goes against the model supported by Ubuntu's developers, and as this is an official support forum, it ought not second-guess the developers.
2) Tutorials/how-tos on enabling graphical root logins. Running your entire X session as root is just a bad idea, but lots of people seem to not realize this. 

But again: nothing in the Ubuntu authentication model in any way restricts the administrative user's privileges. At all.
+1.

In my searching earlier, I was almost amazed at how simple it was to "turn on" the root account.

However, just because it is stupidly simple doesn't make it a good idea.  I am a stupid human and I tend to do stupid things.  Doing stupid things as root user (i.e., hmm, what's this button do?) is just a bad idea.

I prefer the sudo family over root.  The only time I use root is when I need to fix something in recovery mode; as well as that one time someone screwed with the file permissions on the /etc/sudoers file and changed them to 0755 **(bad idea - don't do it)**. I wanted to test ways to fix it, so I did it, booted to recovery mode (because I couldn't sudo it back), and chmod'ed it back to 0440 (or whatever sudo said it should be).

---

### Post by tomthumb99 on 2009-02-10
I am also getting quite tired of typing in 'sudo su' all the time.   The point that I do not hear is that each time I upgrade programs the whole OS is unstable.  It seems that I am fixing the X windows server or re-installing the libc modules each week. So, how much more damage can be done as running with the root ID???
If this OS had only monthly or limited releases that were fully tested, then the point protecting a stable OS would hold.

---

### Post by Tim Sharitt on 2009-02-10
> **p_quarles said:**
> Certain web-based applications are designed to escalate privileges using the more traditional "su" command, and don't know about sudo. Webmin springs to mind.

In any event, this thread is indicative of a common misapprehension. Root isn't "disabled" in Ubuntu, nor are you prevented from "running as root," or even logging into a root shell. The truth is pretty simple: Ubuntu uses sudo and its graphical front-ends for *authenticating* the root user, rather than the more traditional (and, ultimately, less flexible) su command, or the login shell. None of this limits the administrative user's access to root privileges in any way.

My understanding of the policy is that it forbids two specific things:
1) Suggesting that people set a root password. This goes against the model supported by Ubuntu's developers, and as this is an official support forum, it ought not second-guess the developers.
2) Tutorials/how-tos on enabling graphical root logins. Running your entire X session as root is just a bad idea, but lots of people seem to not realize this. 

But again: nothing in the Ubuntu authentication model in any way restricts the administrative user's privileges. At all.

I would like to add that if someone needs to set a root password or login to X as root (which is a really bad idea), this information can be easily obtained from unofficial sources.

---

### Post by jenkinbr on 2009-02-11
> **tomthumb99 said:**
> I am also getting quite tired of typing in 'sudo su' all the time.   The point that I do not hear is that each time I upgrade programs the whole OS is unstable.  It seems that I am fixing the X windows server or re-installing the libc modules each week. So, how much more damage can be done as running with the root ID???
If this OS had only monthly or limited releases that were fully tested, then the point protecting a stable OS would hold.

I have to say here that the Ubuntu Security updates are very important.  To put them off for a month is like suicide for your computer - it leaves it exposed and vulnerable, when a fix is already there.

---

### Post by Romanmir on 2009-02-27
I have a reason for running as root. I was unhappy about the fingerprint reader security program. So I disabled it. Unfortunately, I now can not successfully do anything that requires either su or sudo. So yeah, I actually need the loaded gun handed to me.

/me scurries away from the vendor website to google it as they will apparently not tell me how to enable root.

:rolleyes:

---

### Post by cariboo on 2009-02-27
Actually you still don't need to run as root, start in recovery mode, undo what you did, then reboot. This of course assumes you documented and backed up any configurations files before making changes.

Jim

---

### Post by maybeway36 on 2009-02-27
```
sudo -i
```
I use this all the time.

---

### Post by jenkinbr on 2009-02-27
> **maybeway36 said:**
> ```
sudo -i
```
I use this all the time.

I use it too, but it will not work if sudo doesn't.

> **Romanmir said:**
> I have a reason for running as root. I was unhappy about the fingerprint reader security program. So I disabled it. Unfortunately, I now **can not successfully do anything that requires either su or sudo**. So yeah, I actually need the loaded gun handed to me.

/me scurries away from the vendor website to google it as they will apparently not tell me how to enable root.

:rolleyes:

---

### Post by mister_pink on 2009-02-28
> **Romanmir said:**
> I have a reason for running as root. I was unhappy about the fingerprint reader security program. So I disabled it. Unfortunately, I now can not successfully do anything that requires either su or sudo. So yeah, I actually need the loaded gun handed to me.

/me scurries away from the vendor website to google it as they will apparently not tell me how to enable root.

:rolleyes:

If you've broken sudo then not only will enabling root not help you, but you also won't be able to do it without sudo. Ill give you a clue, the command to enable root starts with "sudo ..." - unless you go into recovery mode, where, as someone else said, you could just fix your problem directly. 

Care to share what you did so you can get advice on how to fix it.

---

