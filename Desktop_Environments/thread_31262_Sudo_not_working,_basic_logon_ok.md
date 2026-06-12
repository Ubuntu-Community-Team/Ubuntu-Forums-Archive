---
title: "Sudo not working, basic logon ok"
date: 2005-05-02
forum: Desktop Environments
---

### Post by marxamuel on 2005-05-02
](*,) I am relatively new to Linux so problems can be expected.  On my other Kubuntu machines it runs quite nicely. Kudos to the community.

On my ancient Toshiba 4020 Laptop:

I seem to be locked out of root.  
When I try run Syaptic it prompts me for the root password, 
I input the same password I used to get into the system and it tells me "incorrect password: Please try again".  
On second attempt I get "conversation with su failed.

I go into the console, type su  get prompt for password input the passord and I get "Authentication Error -Sorry"

I type sudo passwd root and I get a prompt and I am told  "(username) is not int sudoers file.  This incedent will be reported. 

So I can't run updates, install software or go after my sound issue.  How can I get my root logon to behave normally or do I need to nuke the installation and start over?

I have checked posts but it's either not there or I am missing something.  Please help...

---

### Post by shakin on 2005-05-02
I believe if you go into recovery mode (in the bootup menu) you will be able to do things as root.

edit the /etc/group file and find the line for the admin group ('admin' is the first word on the line). Add your name to the end:
```

admin:x:109:msmith,marxamuel

```

That should let you use sudo.

---

### Post by tread on 2005-05-02
Umm .. my two cents .. I could be quite off though.

You need to type 'sudo synaptic'; sudo gives you root privileges but you are not root. So if you are trying to login as root first using the same password, that wouldnt work.

In fact, the root account is disabled by default to prevent people like me from being logged in permanently as root and damaging the system :)

For more information, visit [Ubuntu Unofficial Guide](http://www.ubuntuguide.org)

---

### Post by marxamuel on 2005-05-02
I went into recovery mode and it typed "edit /ect/group and got an error message saying no write permission for file "/ect/group" then gave me back a prompt #

I apologize for my lack of familiarity.  Could you break that down more for me?  How would I make this happen from the command prompt inside the recovery mode?  All help would be appreciated

---

### Post by shakin on 2005-05-02
[QUOTE=marxamuel]I went into recovery mode and it typed "edit /ect/group and got an error message saying no write permission for file "/ect/group" then gave me back a prompt #

I apologize for my lack of familiarity.  Could you break that down more for me?  How would I make this happen from the command prompt inside the recovery mode?  All help would be appreciated[/QUOTE]

Can you please be clear, did you try to edit '/etc/group' or '/ect/group'. The first exists while the latter does not.

Second, 'edit' is not what you want. Sorry, I should have been more clear. Try 'nano /etc/group' Once in nano you can edit the file normally, then hit ctrl-o to save the file and ctrl-x' to exit nano.

---

### Post by marxamuel on 2005-05-02
[QUOTE=shakin]Can you please be clear, did you try to edit '/etc/group' or '/ect/group'. The first exists while the latter does not.

Second, 'edit' is not what you want. Sorry, I should have been more clear. Try 'nano /etc/group' Once in nano you can edit the file normally, then hit ctrl-o to save the file and ctrl-x' to exit nano.[/QUOTE]

That fixed it for me: I now have full functionality inside of root.  Thank you.

This may be inappropriate but do you have any ideas how to get my Yamaha integrated sound going.   Again thank you.  This i s a really great community.
I'm sold.

---

### Post by shakin on 2005-05-02
I'm glad sudo is working now, though it's a bit of a mystery why it wasn't setup properly during installation.

Sorry, no idea about the Yamaha sound card :) Do a board search for 'yamaha' and there are lots of results and some solutions depending on your exact model.

---

