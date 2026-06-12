---
title: "Maintenance stratedgies?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by beforewisdom on 2006-03-17
I'm going to install kubuntu to my hard drive this weekend.

I'm wondering what my maintenace stratedgy should be.  

With Debian the smart thing to do was to run regular apt-get updates and upgrade the software only when there was a compelling feature you wanted.

With Knoppix, after installation, you used a "howto" to "upgrade" to get the equivalent of a Debian Sarge install.  You would manipualte your sources.list to be local to your country and to use Debian stuff.

I've heard that the (k)ubuntu archives are not the same as the Debian archives and are more up to date.   So:

- do I need to run apt-get update ?

- if I just keep installing updates from the ubuntu update notifications do I need to do anything else?   Will I ever need to do a full install again assuming everything works?

- the winhq entry in sources.list doesn't work, does the (k) ubuntu project have another.  If they do should I run apt-get uppdate ?

Will easyubuntu work with (k)ubuntu?

Thanks in advance for the info

Steve

---

### Post by incubus on 2006-03-17
Hello there and welcome aboard.

(K)Ubuntu follows the same philosophy of Debian. But as you said, some packages are more up-to-date at the price of not being as rock-stable (almost infallible) as in good ol'Debian. But that's not a big deal -- I've been using Ubuntu from the beginning and in particular since last two releases I haven't had any serious problem.

So, in other words, regular apt-getting will keep your system shining, especially if you don't tweak it too much and keep using native packages. With that you won't need to reinstall the whole system, just know well the apt-get commands. 

Strange, the winehq repository works for me, but yes Ubuntu has its own package. In Dapper it's very updated, but I'm not sure about Breezy (the current release). I think it's not. But I used winehq's package myself without a problem.

As for easyubuntu, I'm sorry I can't help you. I never tried it, but I'm sure you can talk to the developers easily. They will be happy to get your feedback.

Remember to backup your files first. And searching this forum plus the Ubuntu Wiki will provide you with a lot of useful information.

Good luck,
incubus

---

