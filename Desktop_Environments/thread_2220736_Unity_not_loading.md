---
title: "Unity not loading"
date: 2014-04-29
forum: Desktop Environments
---

### Post by r0t on 2014-04-29
All of a sudden, when I log in to Ubuntu 14.04, I have no top menu bar, no launcher, no dash, only my desktop. Logging in as guest works fine.

Don't know if it's relevant, but if I log in as guest, do ctrl-alt-F1 to open a terminal, log in as my user, run startx to open another gui session, and then try starting Unity from the terminal, it says &#8220;Invalid MIT-MAGIC-COOKIE&#8221;.

Also, [FONT=Courier New]~/.xsession-errors [/FONT] has a lot of error like this:

   [FONT=Courier New] AccountsService-WARNING **: SetInputSources call failed: GDBus.Error: org.freedesktop.Accounts,Error.PermissionDenied: Not Authorized [/FONT] 

What else can I do to troubleshoot?

EDIT: This is what solved it, but only for the current session:

[FONT=Courier New]
sudo apt-get install unity-tweak-tool
export DISPLAY=:0
unity-tweak-tool --reset-unity
unity[/FONT]

Doing this after every reboot now gives me Unity, except for the top menu bar

---

### Post by kc1di on 2014-04-29
this happens sometimes when the .Xauthority file is corrupted.  It's a hidden file in your uses dirctory. 

try boot to a teminal and deleting it. cd to the home folder ```
cd /home/<yourusername>
```  then ```
sudo rm .Xauthority
```  
Then reboot.  it will be regenerated on login.

---

### Post by r0t on 2014-04-29
Thanks, I should have mentioned that I tried that, but with no effect.

---

### Post by kc1di on 2014-04-29
have you checked the permissions on your home directory?  use```
 ls -l 
```to see the permissions.

---

### Post by r0t on 2014-04-29
It looks ok; I am the owner, and I can read and write: `drwxr-xr-x`

---

### Post by r0t on 2014-04-29
Solved it:

Log in and open a terminal (ctrl-alt-F1). If that is not possible from your user account, do it from a guest account, and replace DISPLAY=:0 with DISPLAY=:1 below-

[FONT=Courier New]
sudo apt-get install unity-tweak-tool
export DISPLAY=:0
unity-tweak-tool --reset-unity[/FONT]

---

### Post by r0t on 2014-04-29
....unfortunately the above fix only worked for one session. Still at the same spot as I was this morning... :-/

---

### Post by Awks_Panda on 2014-04-30
I followed the steps contained within the top answer at [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

Compiz config manager will prompt you with a few more plugins that will need to enabled.

Unity has loaded okay for me after the reboot step.

Hope this works for you!

---

