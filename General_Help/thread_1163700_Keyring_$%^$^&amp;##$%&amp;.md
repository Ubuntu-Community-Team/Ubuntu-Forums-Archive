---
title: "Keyring $%^$^&amp;*##*$%&amp;"
date: 2009-05-19
forum: General Help
---

### Post by brad1138 on 2009-05-19
I just reinstalled 9.04 and it asked for a "keyring" password. I had no idea what a keyring was but I entered my normal password. Now every time I boot the message "network manager applet needs access to my keyring but it is lock" comes on. It is very annoying! What the H*** is it and how do I get rid of it?

Thank you,
Brad

---

### Post by JECHO on 2009-05-19
> **brad1138 said:**
> I just reinstalled 9.04 and it asked for a "keyring" password. I had no idea what a keyring was but I entered my normal password. Now every time I boot the message "network manager applet needs access to my keyring but it is lock" comes on. It is very annoying! What the H*** is it and how do I get rid of it?

Thank you,
Brad

I presonally think the whole Keyring thing is dumb but you can go into System > Preferences > Startup Applications and remove the entry for the Keyring Daemon and it wont run the next time you boot up :) thats what i do.

---

### Post by brad1138 on 2009-05-19
I unchecked it and it still asked for password, then I removed it completely and it is still asking me for the password, this is the kind of thing that is going to send me back to XP. I have enough stress in my life without these stupid issues. 

Sorry, just venting a bit, tough day at work.

Thanks,
Brad

---

### Post by JECHO on 2009-05-19
> **brad1138 said:**
> I unchecked it and it still asked for password, then I removed it completely and it is still asking me for the password, this is the kind of thing that is going to send me back to XP. I have enough stress in my life without these stupid issues. 

Sorry, just venting a bit, tough day at work.

Thanks,
Brad

did you reboot?

---

### Post by mcduck on 2009-05-19
> **brad1138 said:**
> I unchecked it and it still asked for password, then I removed it completely and it is still asking me for the password, this is the kind of thing that is going to send me back to XP. I have enough stress in my life without these stupid issues. 

Sorry, just venting a bit, tough day at work.

Thanks,
Brad
It's not asking your password because of the keyring manager starting (so removing keyring manager won't solve the problem, more likely causes new ones), it's a bit more complex than that..

The thing is this, your program need a place to securely store important stuff like encryption keys and network passwords. Keyring Manager provides this for all the programs that need it.

In your case it's most likely Network Manager that needs the password when you log in, and asks Keyring Manager to give it. If you used normal login (with password), the keyring would be unlocked automatically (as you already confirmed you are who you are supposed to be when logging in), but with automatic login you need to unlock the keyring yourself.

The problem is really easy to solve, and preventing the Keyring Manager from working is not the way. Instead, set the keyring password to empty one and Keyring Manager won't ask for it any more.

To do this got to Applications/Accessories/Passwords and Encryption Keys, and on the Passwords-tab right-click the "Passwords:login"-entry and select "Change Password". Enter your current keyring password and leave the fields for new password empty.

(by the way, things like this are no reason to "go back to XP". Instead I recommend doing a quick search on the forums/google, simple "keyring password"-search on these forums lists 250 threads, and most of them have the answer to your problem.. ;))

---

