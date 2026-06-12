---
title: "lightdm stops manual entry of username by default - WHY?"
date: 2014-01-02
forum: Desktop Environments
---

### Post by tsewell.inbox on 2014-01-02
So, I've fixed this, but I'd really like to know why I had to waste twenty minutes of my life on it.

After a recent mini-update, lightdm stopped showing my username as a login option. It also wasn't showing an option to manually specify a login name, though of course I have no idea whether that changed recently or not. I could pick between the first user account ever created, or a guest session. I could not specify my username.

WHY? What possible advantage is there in hiding the little text field in which I can type my username?

Let's clarify, I can still switch to the console (Ctrl+Alt+F1) and login by name. Or SSH to the machine. Or log in as a guest session then su. I can do everything except use X.

Are you trying to save another 2% of screen real estate in your Soviet-minimal login screen? If so, why keep the guest?

The fix is to set greeter-show-manual-login=true in /etc/var/lightdm.conf, and then restart the machine. Restart the machine. Seriously. Reopening X doesn't seem to cause lightdm to re-read its config file, nor does killing every process called lightdm or running as the lightdm user. You have to restart the machine.

If anyone is reading this and wasting their time like I was, learn this. Restart the box. Nothing obvious works.

Remarkably, restarting is the one option lightdm doesn't give you from its default screen. WHY? Why would you ever supply "Shut Down" but not "Restart"? To deter appallingly lazy rogue administrators? To get a little more exercise to those who keep their desktop tower somewhere a little hard to reach?

Once the manual login option is restored and you've used it once, mirabile dictu, lightdm learns my name immediately. It's almost like none of this ever happened.

I suppose someone will tell me that this is all my fault for having multiple user accounts, rather than leaving the UNIX account names to their proper job of identifying the processes of silly services like lightdm. Still, I would prefer it if this feature was either deprecated entirely or it worked. What's the point in allowing multi-user machines and then kicking their owners in the nuts from time to time? Seriously.

Would prefer it if such inexplicably stupid decisions were not taken in future. Thanks.

---

### Post by tsewell.inbox on 2014-01-02
I suppose I should also point out the obvious: I don't use the first ever user account since it was set up by the system administrator, who sets up all our default machines at the office, and I prefer to have an individual identity. Perhaps that's the root of the problem.

---

### Post by deadflowr on 2014-01-03
> **tsewell.inbox said:**
> I suppose I should also point out the obvious: I don't use the first ever user account since it was set up by the system administrator, who sets up all our default machines at the office, and I prefer to have an individual identity. Perhaps that's the root of the problem.

How'd you setup the new user?
And do you know what the sysadmin might have done to the machine before giving it over to you?
There's probably more questions on this, but those two seemed the most interesting.

---

### Post by grahammechanical on 2014-01-03
It is just a machine running computer code. You speak as if the machine is doing things to cause you trouble. Did you click that "Shutdown" option? It usually asks us to confirm and at that point we can confirm to Shutdown or Restart. It is just a different design to what you think it should be. That is all. 

There is no point in insulting the developers. Not on this forum because very few developers actually give assistance on this forum and such behaviour is contrary to the forum code of conduct. And it prevents me from offering assistance. And as a unpaid volunteer I am free to make my own choices.

[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

Oh, by the way, some updates change configuration files that are only read by the OS at boot time. So, it only at a reboot that something like this problem is corrected.

---

