---
title: "Feisty not saving beryl-manager in start-up session"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by StevenX on 2007-04-23
So after days of fighting with Feisty over direct rendering I've finally given in and clean installed Feisty. Now I've got Beryl back up and running and my lovely flashy desktop back to normal.

However, I have to run beryl-manager from the terminal every time I want to start Beryl
When I go to System > Preferences > Sessions, and add "beryl-manager," there it disappears when I close and reopen the Sessions window. Therefore, Beryl doesn't start up at next login as it should.

Does anyone have any idea why this is, and how to get Beryl to just work when I login?

---

### Post by Snowcat on 2007-04-23
Shouldn't you just add "beryl", not "beryl-manager"? and also "emerald --replace"? That's what I have.

---

### Post by orange2k on 2007-04-23
I think you have to add beryl, beryl-manager and emerald for this to work...

---

### Post by StevenX on 2007-04-23
I think the problem is Feisty not saving anything I put in there at all.. It's not that I have the wrong things there as far as I know..
When I add an entry, I can see it in the "Additional Startup Programs," section. But if I then close and reopen the "Sessions," window, whatever I'd just added is now not present any more...

---

### Post by StevenX on 2007-04-24
Never mind, I found some terminal commands to run which created an autostart which works just fine - should have spent a bit longer reading through the wiki before posting!
The session window's behaviour is still quite strange though!

---

### Post by beefcurry on 2007-04-24
So its not just me experiecing this problem. I'll report this as a bug.

---

### Post by d-mac on 2007-05-09
I've also had this problem.  Additionally, when I log in, now the title bars do not appear on any windows until I start Beryl-Manager manually.  Has anyone found a solution to this yet?

Thanks.

---

### Post by Callandor64 on 2007-05-15
Hey there,

I had a problem just like you describe.  I think it might have been related to a messed up permission on beagle install or possible uninstall.

Either way, the solution that worked for me was changing a folder permission and the file within it:

~/.config/autostart

The above folder was set to have root access only.

```
sudo chown <your username> ~/.config/autostart
```
You might want to check all the files in there are set to the right permissions too.

Hope this helps ya,

Callandor64

---

### Post by viciouslime on 2008-01-22
I tired repairing this file as suggested, but it didn't help :(

The solution I found was simply to delete it using:

```
sudo rm -rf ~/.config/autostart
```

The next time I started the sessions app it recreated it and it worked flawlessly :D Warning: You will of course loose any custom-start-up entries that weren't already present in the session manager when you installed ubuntu!

---

