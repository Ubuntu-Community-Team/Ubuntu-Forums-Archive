---
title: "SHIFT+Backspace reboots UI in Beryl"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by AgelessDrifter on 2007-04-14
How do I change this? I type a lot, and I mess up and hit these keys together a lot. I can't be having this ^_^;

---

### Post by K.Mandla on 2007-04-14
(Shifted to Desktop Effects. ;) )

---

### Post by AgelessDrifter on 2007-04-14
Oops ^_^;

---

### Post by AgelessDrifter on 2007-04-15
Anyone? I've looked all over for this setting in Beryl Manager, and I can't find where to change it. I've had the UI reboot on me 3 times while writing this post alone.

---

### Post by aidanr on 2007-04-15
add ```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
``` to your startup programs

---

### Post by konungursvia on 2007-04-15
It's not Beryl, it's gnome. It can be changed, I changed mine but I forget how. It's in a post already. Do a search here for shift-backspace and you'll find out how to reassign that. It's about two lines in the terminal, quite easy. [Edit: well there it is.]

---

### Post by AgelessDrifter on 2007-04-15
edit: Oh, thanks for the responses, guys. That was quick. I found it on google like two seconds after I made my last post, and I didn't think anyone had responded in that time. ^_^;

---

### Post by lotacus on 2007-04-18
would have been helpful if you posted your findings. :P

---

### Post by MindRiot on 2007-04-19
Read this:

[http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/]("http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/")

BTW: As discussed in the link above, I chose to create a startup script. Since I was unable to make the xmodmap options work.

I created a new text file called key_rebind and added the line xmodmap -e 'keycode 22 = BackSpace BackSpace Terminate_Server' 
Under /home/yourusername/  I created a hidden file called .scripts and then created another folder under that one called startup, so I placed the key_rebind text file in  /home/yourusername/.scripts/startup.   I typed chmod +x /home/yourusername/.scripts/startup/key_rebind in the terminal to make the file executable, then I opened Sessions from System/Preferences and added /home/yourusername/.scripts/startup/key_rebind under the startup tab..

---

### Post by kvonb on 2007-04-19
Easy, cut off the offending finger with a rusty knife!

Works every time for me, although I have a real problem holding cups, and pens, and......

hahahahaha :lolflag:

---

