---
title: "[SOLVED] Su won't accept password"
date: 2008-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wgilbert5 on 2008-07-06
I have a real problem running Ubuntu on my Dell 1505.  I cannot get the terminal to accept my password when I try to su into it.  I've even tried to sudo in as I've had to do in other linux distros.  Still nothing.  I can't use apt-get install or any other useful command if I can't get in.  I am running Ubuntu 7.04.  Hope someone can help me, please.  Thank you.

---

### Post by lisati on 2008-07-06
1) try "sudo" instead of "su"
2) Don't panic if your password doesn't show when you type - this is normal, and is part of Ubuntu's security. Just type it as usual and press 'Enter'

---

### Post by OffHand on 2008-07-06
you first have to enable root with this command ```
sudo passwd root
```

p.s. with most things you do sudo should be sufficient.

---

### Post by unutbu on 2008-07-06
If you come from a background in other linux distros, you may be used to su'ing root. In ubuntu, it is more customary to just prefix individual commands with sudo.
For instance, to apt-get install, you run

```
sudo apt-get install <package>
```

Your password as wgilbert5 (or whatever it is on your machine) will work as long as you are part of the admin group. (Run `groups` to check).

Though not recommended, if you want to use a root shell, here is how to do it:
```

dow@11000:~% su          # su alone does not work
Password:                # even if you put your password  
su: Authentication failure
Sorry.
dow@11000:~% su root     # interestingly, this fails too
Password: 
su: Authentication failure
Sorry.
dow@11000:~% sudo        # sudo is not used this way
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
dow@11000:~% sudo su     # This gives you a root shell
Password: 
root@11000:/home/dow# exit
exit
dow@11000:~% sudo -i     # This also gives you a root shell
root@11000:~# exit
exit
dow@11000:~% sudo bash   # This too
root@11000:~# exit
exit

```

---

### Post by Tomatz on 2008-07-06
> **wgilbert5 said:**
> I have a real problem running Ubuntu on my Dell 1505.  I cannot get the terminal to accept my password when I try to su into it.  I've even tried to sudo in as I've had to do in other linux distros.  Still nothing.  I can't use apt-get install or any other useful command if I can't get in.  I am running Ubuntu 7.04.  Hope someone can help me, please.  Thank you.

No text will appear while typing the password. This is a security measure ;)

---

### Post by Steveway on 2008-07-06
> **OffHand said:**
> you first have to enable root with this command ```
sudo passwd root
```

p.s. with most things you do sudo should be sufficient.

Don't do that. Enabling the root-account is a security-risk and not recommended to do.
Use sudo and gksu to do administrative tasks that normally require root access.

---

### Post by gbrainin on 2008-07-06
Assuming you've tried all of the above, using both what you think the super-user password and your user account's password should be, you may have a permissions problem.  For example, maybe your password got re-set or you forgot it, or the user account you're logging in under doesn't have sudo permissions.  Fixing these things is simple, once you have super-user privileges--and that's what recovery mode is for.

Reboot the machine, and when you get to the GRUB menu (you may need to press Esc to make it appear), select the same kernel you usually use, but the recovery mode line directly below the one you usually boot into.  This will boot the machine in single-user mode, and you then have root privileges (**VERY DANGEROUS-BE CAREFUL**) to do things like re-setting passwords.

---

### Post by wgilbert5 on 2008-07-07
Thank you so very much, folks.  I used Offhands suggestion and it worked like a charm.  I have thanked each of you and am very proud of the quick, no-nonsense answers to my original query.  I really appreciate it.  Bill

---

### Post by Steveway on 2008-07-07
> **wgilbert5 said:**
> Thank you so very much, folks.  I used Offhands suggestion and it worked like a charm.  I have thanked each of you and am very proud of the quick, no-nonsense answers to my original query.  I really appreciate it.  Bill

That was a very stupid thing to do. You just lowered the security of your system by a big magnitude. I hope nothing bad happened yet, you should immediatly take a look for a how-to about reverting that.

---

### Post by Tomatz on 2008-07-07
> **Steveway said:**
> That was a very stupid thing to do. You just lowered the security of your system by a big magnitude. I hope nothing bad happened yet, you should immediatly take a look for a how-to about reverting that.

Oi!

He is a new user, no need for that :mad:

He only followed instructions given by another poster.

---

### Post by Steveway on 2008-07-07
> **Tomatz said:**
> Oi!

He is a new user, no need for that :mad:

He only followed instructions given by another poster.

Yup and even though those instructions don't seem as malicious as the often heard sudo rm...(You know which I mean.), it can be even more dangerous in the long run. Why? You ask. Because it lowers the security of your system and bad people could break into it more easily, and instead of just deleting your data he could spy on you and gather critical data like banking-information etc.
Enabling the root-account is not recommended for a reason.
Yes this is a "worst-case-scenario" but worse things allready happened.

---

### Post by Tomatz on 2008-07-07
> **Steveway said:**
> Yup and even though those instructions don't seem as malicious as the often heard sudo rm...(You know which I mean.), it can be even more dangerous in the long run. Why? You ask. Because it lowers the security of your system and bad people could break into it more easily, and instead of just deleting your data he could spy on you and gather critical data like banking-information etc.
Enabling the root-account is not recommended for a reason.
Yes this is a "worst-case-scenario" but worse things allready happened.


Yes WE all know it's a security risk but cut the guy some slack. He is probably not stupid, just new to linux.


The guy who told him to do it is the plumb!

---

### Post by unutbu on 2008-07-07
What is so horrible about giving root a password?
Many other linux distros work that way.
How is root's password any less secure than the password of a normal user who is a member of the admin group?

---

### Post by jocko on 2008-07-07
> **unutbu said:**
> What is so horrible about giving root a password?
Many other linux distros work that way.
How is root's password any less secure than the password of a normal user who is a member of the admin group?

If you have an active root account, a potential attacker will try to login as root, and "only" have to crack your root password to get in.
Without a root account, such attacks will always fail (as the user "root" can't log in). And, if he KNOWS you have no root account, he will have to guess both your username and password, so it will be much more difficult...

---

### Post by unutbu on 2008-07-07
This is a very weak layer of protection. Aren't usernames pretty much public information? I would not be the least surprised if I am giving away my username to every website I visit (maybe through the environment variables?)

Normal Ubuntu users are not trained to keep their usernames private, so shouldn't we regard them as essentially public?

---

### Post by OffHand on 2008-07-08
Use a strong password. Case closed :guitar:

---

### Post by Steveway on 2008-07-08
> **unutbu said:**
> This is a very weak layer of protection. Aren't usernames pretty much public information? I would not be the least surprised if I am giving away my username to every website I visit (maybe through the environment variables?)

Normal Ubuntu users are not trained to keep their usernames private, so shouldn't we regard them as essentially public?

No, usernames are not published by any software without you explicitely doing so. (Like posting it on the net manually.)
We use sudo because it adds this security it is there for a reason, the Ubuntu-devs are not stupid so don't implicate that by critisizing sudo. (Even MacOSX uses sudo, btw.)
Also, crackers try to break into a PC by using commonly used usernames (root is the best candidate on a Unix-system.) and then trying out a lot of passwords. This happens most of the time automatically by software. So if you don't have root then the attacker has to first guess your username (impossible, how will you know the username of a PC you try to break in if you don't know whom it belongs to, and even then.).

---

### Post by OffHand on 2008-07-08
> **Steveway said:**
> No, usernames are not published by any software without you explicitely doing so. (Like posting it on the net manually.)
We use sudo because it adds this security it is there for a reason, the Ubuntu-devs are not stupid so don't implicate that by critisizing sudo. (Even MacOSX uses sudo, btw.)
Also, crackers try to break into a PC by using commonly used usernames (root is the best candidate on a Unix-system.) and then trying out a lot of passwords. This happens most of the time automatically by software. So if you don't have root then the attacker has to first guess your username (impossible, how will you know the username of a PC you try to break in if you don't know whom it belongs to, and even then.).
And the Debian devs are not stupid either and they leave root enabled.... Enabling root is as secure as the password that you use.

---

### Post by jocko on 2008-07-08
> **OffHand said:**
> And the Debian devs are not stupid either and they leave root enabled.... Enabling root is as secure as the password that you use.

Enabling root is as secure as the password you use... but the username (root) is very easy to guess...

Let's see it in this extremely simplified way:
If the username and passwords were both numbers between 0-999, the chance of randomly guessing the username would be 1 in 1000 and the chance of randomly guessing the correct password is the same.
That means the probability of someone guessing both username and password correctly, at the same time, would be one in a million, whereas if you use a username that is already known, it would be only 1 in 1000.
Let's say the timeout between failed login attempts is 3 seconds (I think that's what I get when I mistype my password).
That means it would take only 3,000 seconds (=50 minutes) to test every possible password, but it would take 3,000,000 seconds (=34 days, 17 hrs, 20 mins) to test every possible username/password combination. Which would be safer, do you think?

I know this was overly simplified as the number of possible passwords and usernames is very much greater than 1000, but the relative difference would be about the same.
Plus, with sudo instead of root login, your computer is a *little* bit safer from your own mistakes [but of course I have trashed my system once or twice using "sudo rm -rf" in the wrong place...].

---

