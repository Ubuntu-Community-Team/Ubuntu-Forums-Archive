---
title: "Disable password prompt"
date: 2009-03-23
forum: General Help
---

### Post by Meta03 on 2009-03-23
I would like to disable the prompt for password I get when I change certain things. How can this be done?

---

### Post by bodhi.zazen on 2009-03-23
Moved to general help.

What may I ask are you talking about ? What password, where ?

In general we do not support such activity but expect you to be able to read the man pages and figure it out for yourself.

The need for a password is there for your protection, even if yo feel you do not need it.

---

### Post by cariboo on 2009-03-23
Have a look at [this]("http://help.ubuntu.com/community/RootSudo"), it will explain how the Ubuntu security model works. Having no password is totally unsecure, you leave your self open to all sorts of bad things.

Jim

---

### Post by Meta03 on 2009-03-24
I have it on a computer at home that is not connected to the internet. I am the only one that uses it, so security is not an issue. 

I am experimenting with Linux to see if I want to switch from Windows Vista and having to type in a password every few minutes is a nuisance for me at this time.

---

### Post by Meta03 on 2009-03-24
> **bodhi.zazen said:**
> In general we do not support such activity but expect you to be able to read the man pages and figure it out for yourself.

I have been researching this for a while, but was unable to find a solution. I thought coming here to the "help" forum would be a good idea. It appears I might have been mistaken...

PS: Interesting sig.

---

### Post by kanikilu on 2009-03-24
> **Meta03 said:**
> I have it on a computer at home that is not connected to the internet. I am the only one that uses it, so security is not an issue. I think it's really more to protect you from yourself, rather than the outside ;)

> I am experimenting with Linux to see if I want to switch from Windows Vista and having to type in a password every few minutes is a nuisance for me at this time. The thing I like most about Ubuntu (Linux in general) is choice. If you *choose* to run as root all the time, no one can stop you, but 1) as already stated, it's **not** a good idea, and 2) I honestly don't even know how to, off the top of my head, since I've never wanted to do that. It's in the documentation on the website, though. Just search for it.

Although, there is a third option. Like you, I did not like the short sudo timeout. What I did, and what you might consider trying first before resorting to running as root full-time, is to add something like "timestamp_timeout=60" to the end of your Defaults line in the /etc/sudoers file. This will increase the default timeout from 15 minutes to an hour. Here is the guide in the documentation: 

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by mocoloco on 2009-03-24
Meta03 doesn't want to run as root all the time, just disable the prompt for password when using sudo, and seems to understand the risks and wants to go ahead.
Look at [this thread]("http://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/") on linuxquestions, I used to have a better source but can't find it, but it says what you need to do.
It's also possible to not be prompted for password for just some applications.  I've done that for my nvidia-settings-manager because I use it a lot switching between different monitor setups.

---

### Post by bodhi.zazen on 2009-03-24
Well, we expect users to read and understand the manual if they wish to understnad security.

This policy is often mis-understood.

The point is that these changes have potential security risks and as such as staff we feel a responsibility to educate users if they wish to make changes.

The best reference, IMO, is here :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

If after reading that you have a technical question please ask.

But please do not post the "solution" to this question without education.

And with that I think the question is asked and answered so I am going to close this thread now.

Please also see : [New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

Not that this link directly applies, but it outlines the philosophy of the staff & why we ask for users to be educated on security.

---

