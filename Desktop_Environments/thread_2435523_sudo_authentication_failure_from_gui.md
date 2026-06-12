---
title: "sudo authentication failure from gui"
date: 2020-01-22
forum: Desktop Environments
---

### Post by sturgl on 2020-01-22
Hello!

I've a new install of Lubuntu 19.10 that I'm working with.  Any time an application in the GUI requires elevated rights, I receive an authentication error.  I am of course entering my pw correctly and my user is a member of the sudo group.  In a terminal session, all is well.  When logged-in to the UI, whether remotely or locally, anything that needs root fails to authenticate when I enter my password - Discover, muon, various other applications.  .xauthority appears to be permissioned properly.

I could really use some help here.  None of my searching the interwebs has panned out.

Thank you!

---

### Post by CelticWarrior on 2020-01-22
Is your keyboard layout set correctly?

---

### Post by sturgl on 2020-01-22
I'd wondered that too, since the GUI is consistently acting like I've typed the wrong characters in the password dialogue.  I can type normally in Featherpad, can search the Web, etc. - so I think it's set up correctly but I'll check!

I should mention that I have two different accounts, both members of sudo (I need the 2nd one for xRDP).  Both suffer from the same problem.

---

### Post by CelticWarrior on 2020-01-22
The problem with incorrect keyboard layouts is the special characters. If your password includes special characters and the keybioard layout doesn't match what you have that surely is the problem.

---

### Post by sturgl on 2020-01-22
The keyboard is a "generic 104-key keyboard".  That's probably not entirely accurate, since I remote in from a laptop - but it seems close enough.  However, maybe you're on to something.  im-config yields the following output:
 Current configuration for the input method:                              &#9474;
  &#9474;  * Active configuration: missing (normally missing)                      &#9474;
  &#9474;  * Normal automatic choice: fcitx (normally ibus or fcitx or uim)        &#9474;
  &#9474;  * Override rule:                                                        &#9474;
  &#9474; zh_CN,fcitx:zh_TW,fcitx:zh_HK,fcitx:zh_SG,fcitx:ja_JP,fcitx:ko_KR,fcitx: &#9474;
  &#9474; vi_VN,fcitx                                                              &#9474;
  &#9474;  * Current override choice:  (en_US)                                     &#9474;
  &#9474;  * Current automatic choice: fcitx                                       &#9474;
  &#9474;  * Number of valid choices: 2 (normally 1)

---

### Post by sturgl on 2020-01-22
I'm in good shape there.  Typed my pw into featherpad, and it's correct.

---

### Post by CelticWarrior on 2020-01-22
Sorry for not reading attentively enough your OP... The fact that you can login to the desktop rules out the keyboard layout mismatch. And ig the user is still a member of sudoers it should be fine.

Do you have another user also in sudoers? In that case you should get a dropdown menu and the other user could possibly be the default one...

---

### Post by sturgl on 2020-01-23
I do have another user in sudo. It exhibits exactly the same problem: no issues in terminal, consistent authentication failure when the GUI wants root.

---

### Post by sturgl on 2020-01-23
Anyone?  This one's a bit of a head scratcher.  Thanks in advance!

---

### Post by CatKiller on 2020-01-23
The difference between the two is that the command line uses sudo and the GUI uses polkit. Other than "your polkit seems to be broken" I don't have anything to add, though.

---

### Post by sturgl on 2020-01-23
> **CatKiller said:**
> The difference between the two is that the command line uses sudo and the GUI uses polkit. Other than "your polkit seems to be broken" I don't have anything to add, though.

Well, that's a lead.  I'll dig into it.  Thanks.

---

### Post by sturgl on 2020-01-29
Welp, I couldn't get it figured, but I'm not worrying much about it.   This install is for a Plex server.  I really only need access for  maintenance and I do most everything via command line.  Just  aggravating, particularly since I think I broke it while beating xRDP  into submission.

---

