---
title: "Can't log into root"
date: 2022-09-01
forum: Desktop Environments
---

### Post by jerrywo on 2022-09-01
So I tried to log into the Synaptic Package manager this evening.  All attempts failed
So I opened a terminal and typed sudo -i
typed in my password and got'"jerryw is not in the sudoers file.  This incident will be reported."

Yikes

What to do?

Jerry
Warrenton, VA

---

### Post by ActionParsnip on 2022-09-02
Your user needs to be in the sudo group. The first account you setup when you installed Ubuntu has this access. If you want to add your jerryw user to the sudo group, then run:
```

usermod -a -G sudo jerryw

```

You can now log off and on and use sudo as jerryw

---

### Post by jerrywo on 2022-09-02
When trying to log into the Synaptic Package manager, it fails.
In the terminal when I type "usermod -a -G sudo jerryw" I get:
usermod: Permission denied.
usermod:  cannot lock /etc/passwd; try again later

Jerry

---

### Post by ActionParsnip on 2022-09-02
Yes because adding users to groups is an administrative action so needs sudo. You can't just add your user to groups. It'd make Ubuntu the least secure OS ever as anyone can get any access they want....
Is "jerryw" the first account when you first installed Ubuntu?

---

### Post by jerrywo on 2022-09-02
Yes, jerryw is the first (and only account) when first installed Ubuntu

Jerry

---

### Post by jerrywo on 2022-09-02
Also, I was trying to set up WSJT-X, a ham radio program and had some issues with dialout (no permission)
I ran:  sudo usermod -G dialout jerryw

Jerry

---

### Post by ActionParsnip on 2022-09-02
Then use this
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)
Instead of resetting your password, run the 2 commands below
```

usermod -a -G sudo jerryw
reboot

```

---

### Post by jerrywo on 2022-09-02
I get
usermod:  Permission denied,
usermod:  cannot lock /etc/passwd; try again later.

---

### Post by ActionParsnip on 2022-09-02
Did you run
```

mount -o remount,rw /

```
First?

---

### Post by jerrywo on 2022-09-02
I did not....I gave your note too quick a read...sorry,  I'll give it a try

Jerry

---

### Post by jerrywo on 2022-09-02
This is a little complicated but not outside of my grasp - but I'm gonna hit the sack and 
tackle this tomorrow PM.  

Many many thanks
tomorrow
Jerry

---

### Post by jerrywo on 2022-09-03
Thank you, thank you Mr. ActionParsnip.
I am back in business

Jerry

---

### Post by ajgreeny on 2022-09-03
Great news! 
Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

