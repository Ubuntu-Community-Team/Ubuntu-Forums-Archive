---
title: "Disable password requirement for switching users"
date: 2009-09-09
forum: Desktop Environments
---

### Post by osx on 2009-09-09
I have two accounts on my Ubuntu 9.04 install. One account has auto login enabled.

When I use the switch user function to log into the other account, and then attempt to come back to the original account, I am prompted for the password of the original account (the one that has auto login enabled).

Does anybody know if there is a way to either prevent the switch user function from locking the account or requiring a password to switch back?

Thanks.

---

### Post by earthpigg on 2009-09-09
system -> admin -> login window prefs

security tab -> enable timed login

---

### Post by osx on 2009-09-10
> **earthpigg said:**
> system -> admin -> login window prefs

security tab -> enable timed login

I've enabled that, but it still doesn't work. I still get prompted for the password when I try to switch back to the other account that has already logged in.

---

### Post by blur xc on 2009-09-10
> **osx said:**
> I've enabled that, but it still doesn't work. I still get prompted for the password when I try to switch back to the other account that has already logged in.

I'm also interested in this.  We have two primary users on our home pc, and we switch back and forth often.  This would be a welcome option.

BM

---

### Post by CoolHand on 2009-09-10
You could always manually set the password in the /etc/shadow file to "U6aMy0wojraho".  That is the hash for a blank password.

Then you should be able to just smack return to log in.

---

### Post by blur xc on 2009-09-10
> **CoolHand said:**
> You could always manually set the password in the /etc/shadow file to "U6aMy0wojraho".  That is the hash for a blank password.

Then you should be able to just smack return to log in.

Missing the point- we want a password to log in.  But once logged in, it would be nice to have the option to switch back and forth between two logged in users w/o having to enter the password every time.

BM

---

### Post by CoolHand on 2009-09-14
I don't think that is likely to be possible as it goes against all things secure.  If you shut down your PC between sessions though you might consider blanking the passwords and only setting a boot password in grub.  That way you need the PW to get into the PC but your users can be blank passwords.  All I can think of.  Good luck.

---

### Post by osx on 2009-10-29
> **CoolHand said:**
> I don't think that is likely to be possible as it goes against all things secure.  If you shut down your PC between sessions though you might consider blanking the passwords and only setting a boot password in grub.  That way you need the PW to get into the PC but your users can be blank passwords.  All I can think of.  Good luck.

Thanks for your suggestion and I understand what you are saying, but it seems like disabling the password for switching users would be an option.

I know it goes against all things secure, but so does auto-login, non-encrypted home directories, and the option to not lock the screen when screensaver is active.

If such a feature were available, I certainly wouldn't expect it to be enabled by default.

Maybe somebody reading this thread knows how to submit such a feature request. If so, please respond so I can submit one.

Thanks.

---

### Post by osx on 2009-12-12
There isn't a fix for this at the moment, but anybody wanting such a feature/ability can vote to implement it at Ubuntu's Brainstorm site at [http://brainstorm.ubuntu.com/idea/22134/]("http://brainstorm.ubuntu.com/idea/22134/")

---

### Post by yourarunbabu on 2009-12-13
> **osx said:**
> I have two accounts on my Ubuntu 9.04 install. One account has auto login enabled.

When I use the switch user function to log into the other account, and then attempt to come back to the original account, I am prompted for the password of the original account (the one that has auto login enabled).

Does anybody know if there is a way to either prevent the switch user function from locking the account or requiring a password to switch back?

Thanks.
You may better try for a grease monkey script for swithching multiple gmail accounts.
[http://userscripts.org/scripts/show/16341](http://userscripts.org/scripts/show/16341)

---

### Post by osx on 2009-12-14
> **yourarunbabu said:**
> You may better try for a grease monkey script for swithching multiple gmail accounts.
[http://userscripts.org/scripts/show/16341](http://userscripts.org/scripts/show/16341)

Thank for your suggestion. The grease monkey script may work for gmail issues, but doesn't impact the total user environment (e.g., internet bookmarks, desktop settings, documents, etc). There needs to be a mechanism for making it easier to switch between user accounts.

It's unfortunate, but so many people seem to look at needs such as this in a vacuum by saying such a feature shouldn't be implemented because of security risks. However, they should also realize that not every situation needs total lockdown. I use profiles for each family member out of convenience, not security. There's no data on the system that needs protection. It's used primarily for surfing the 'Net and doing web-based email; however, I like my environment customized differently than my spouse and kids, and the same with them.

I don't see why such a feature can't be developed and implemented, but not enabled by default to help protect security for those that do need it. That is why I am encouraging people to vote positively for the brainstorm project mentioned above.

---

### Post by BlackShift on 2010-05-14
Same situation here.

I 'fixed' it by removing the ability to lock the screen completely by using gconf-editor to set /desktop/gnome/lockdown/disable_lock_screen to True.

[http://ubuntuforums.org/showpost.php?p=9297314&postcount=25](http://ubuntuforums.org/showpost.php?p=9297314&postcount=25)
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/501864](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/501864)

---

