---
title: "Question about Cron Jobs"
date: 2010-11-10
forum: Desktop Environments
---

### Post by throese on 2010-11-10
So, last night, I did a little research and think using Cron Jobs are awesome. However, I have a slight problem.

I have a file that I made called "update_manager.sh" and have it set up to use the update manager, but you have to hit "y" for yes or "n" for no. I have it set so the update manager starts at 2:05 EVERY day of the week at that time specifically. But, my problem is, I don't wanna stay up that late just to press "y" every time. How do I make it so "y" is always chosen?

---

### Post by u-slayer on 2010-11-10
echo y | updatemanager.sh

---

### Post by throese on 2010-11-10
Thanks. I'm sure it will work

---

### Post by throese on 2010-11-11
And it didn't work, the "echo y | update_manager.sh" part. What do I try now?

---

### Post by CharlesA on 2010-11-11
So you want to apply updates every day at 2am?

Why not just use unattended updates? You can do normal updates with it by uncommenting that line in /etc/apt/apt.conf.d/50unattended-upgrades)

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

If that's not what you want, you can just use ***apt-get upgrade --assume-yes***, but that may upgrade something you didn't want upgraded.

---

### Post by throese on 2010-11-11
Charles: But I only have unlimited bandwidth from 2 AM to 7 AM and I can't stay up that late. That's why I want to set a Cron Job to do it. I'm sure I want everything updated, but I'll always check during the day before letting the cron job update.

---

### Post by CharlesA on 2010-11-12
If that's the case, you can always just have it run this:

```
#!/bin/bash
apt-get update && apt-get upgrade --assume-yes
```

Throw it in a cronjob and that should get it working.

---

### Post by throese on 2010-11-12
I don't understand the "--[insert word here]" part. Why do people do that?

Example: shutdown --help

or when you're backing stuff up.

Ex: --exclude=/mnt

So what would "--assume-yes" do?

---

### Post by CharlesA on 2010-11-12
See here:

```
--assume-yes
    Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package or removing an essential package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.
```

It's just a switch.

---

### Post by throese on 2010-11-12
It didn't work Charles. =(

---

### Post by CharlesA on 2010-11-13
Did you use the full path, I forgot to mention that.

Also add "**> /home/username/somefile 2>&1**" to the end of the entry in the crontab to see what it's doing.

---

### Post by throese on 2010-11-13
Doesn't matter, I updated it last night. Stayed up till 5:00 AM

---

