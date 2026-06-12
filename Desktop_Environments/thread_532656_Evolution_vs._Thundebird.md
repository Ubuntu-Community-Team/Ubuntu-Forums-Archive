---
title: "Evolution vs. Thundebird"
date: 2007-08-23
forum: Desktop Environments
---

### Post by xp_newbie on 2007-08-23
If Firefox is the default browser for Ubuntu, why isn't Thunderbird the default email client for Ubuntu as well?

Thanks,
Alex

---

### Post by aysiu on 2007-08-23
> **xp_newbie said:**
> If Firefox is the default browser for Ubuntu, why isn't Thunderbird the default email client for Ubuntu as well?

Thanks,
Alex
Evolution is Gnome's default mail client. For this reason, many Gnome purists think the Epiphany (instead of Firefox) should be Ubuntu's default web browser. Firefox's popularity, however, is probably its reason for being the exception to the general use-Gnome-native-apps policy.

---

### Post by orange2k on 2007-08-23
Evolution is far more advanced than Thunderbird - its like Outlook vs Outlook express.

---

### Post by Dark Star on 2007-08-23
> **orange2k said:**
> Evolution is far more advanced than Thunderbird - its like Outlook vs Outlook express.
Evolution ftw. Very easy and too many features :;)

---

### Post by marcozs on 2007-08-23
Probably most people just need a mail application and not a PIM like Evolution, so Thunderbird probably fits most people's needs. By the way it's really easy to install Thunderbird, so I don't see a problem in having Evolution as default...

---

### Post by AZzKikR on 2007-08-23
I just like the way how Evolution integrates with the date-time applet. Evolution does the mail very nicely, so I don't need Thunderbird.

---

### Post by xp_newbie on 2007-08-23
Guys, thank you very much for your replies.

Unfortunately, I need a solution that works on both Ubuntu and... Windows 2000.

So I tried the latest & greatest version of Evolution for Windows that can be downloaded here:

[http://shellter.sourceforge.net/evolution]("http://shellter.sourceforge.net/evolution")

And the result was disastrous. :(

Not only it refused to run (exiting with an invalid memory access, which is an indication of very serious bugs), but until it actually showed signs of being invoked, it took forever... So slow, especially comparing to Thunderbird. Is Evolution written in Java?

Thanks,
Alex

---

### Post by Golyadkin on 2007-08-24
Well, I really love Evolution too, but I don't use it. Simply because I need it to be the same on both my Windows XP and Ubuntu partitions. I share the mailbox directories on the NTFS by symlinking them to ~/.thunderbird, which works perfectly. I use Thunderbird 2.0.0.6 with Enigmail on both platforms.

---

### Post by xp_newbie on 2007-08-24
> **Golyadkin said:**
> Well, I really love Evolution too, but I don't use it. Simply because I need it to be the same on both my Windows XP and Ubuntu partitions. I share the mailbox directories on the NTFS by symlinking them to ~/.thunderbird, which works perfectly. I use Thunderbird 2.0.0.6 with Enigmail on both platforms.

Yes, that's the solution I am using for now - Thunderbird on both Windows and Ubuntu.

What is Enigmail? Why do you use it?

Thanks,
Alex

---

### Post by ntlam on 2007-08-24
I once failed to set up my email account with evolution so I installed thunderbird. Thanks god it was much easier to get it work.

---

### Post by ntlam on 2007-08-24
and some one said that thunderbird on windows is more secured as compared with outlook. I am not really sure about that.

---

### Post by Wolki on 2007-08-25
> **xp_newbie said:**
> So slow, especially comparing to Thunderbird. Is Evolution written in Java?

No, but the windows version isn't maintained or supported, and should not be used as an indication of evolution's quality. I don't need windows compatibility, so I'm free to enjoy all the evo goodness I want. :)

---

### Post by Golyadkin on 2007-08-27
> **xp_newbie said:**
> 
What is Enigmail? Why do you use it?


EnigMail allows me to use public key infrastructure encryption software to protect the confidentiality and integrity of my email messages. In short: it makes it super easy to email in the most secure way possible. [http://enigmail.mozdev.org/](http://enigmail.mozdev.org/)

---

### Post by xp_newbie on 2007-08-27
> **Golyadkin said:**
> EnigMail allows me to use public key infrastructure encryption software to protect the confidentiality and integrity of my email messages. In short: it makes it super easy to email in the most secure way possible. [http://enigmail.mozdev.org/](http://enigmail.mozdev.org/)

Wow! This is a great tool. Good to know about this. Perhaps we users can take back some of our privacy. :) 

A tiny question: If I send an email using EnigMail, must the recepient have EnigMail as well? If not, how does this work?

Thanks,
Alex

---

### Post by Golyadkin on 2007-08-28
If you sign the message, the receiving person doesn't need to have EnigMail, it will just show a signature at the bottom. In order to verify your signature, the receiving person needs to have a GnuPG or OpenPGP compliant email client and your public key. The same holds for encrypted email. 

You should read up a little on public key infrastructure.  [http://en.wikipedia.org/wiki/OpenPGP](http://en.wikipedia.org/wiki/OpenPGP)
[http://enigmail.mozdev.org/help.html](http://enigmail.mozdev.org/help.html)

What you do is simple, you create your own key pair, a private and a public key. You give your public key to people you trust, and you keep your private key very safe. The private key is protected with a password. 
To sign an email (or any other file) you only have to enter your password. The receiving end can verify that the email is sent by you (because it can only have a valid signature if the sender has the right password) and also that it was not modified by someone else. 
To encrypt a file, you encrypt it to the public key of the receiver. This means that ONLY the receiver can decrypt it.

---

