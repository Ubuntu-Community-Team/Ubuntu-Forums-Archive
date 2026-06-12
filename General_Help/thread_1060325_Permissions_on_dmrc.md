---
title: "Permissions on dmrc"
date: 2009-02-04
forum: General Help
---

### Post by fearful on 2009-02-04
I'm having problems when I login to ubuntu.

I get an error message something about my $HOME and not having right privileges I need to be owner and 644 permissions and I have done this more then one time already, with clean installs.

After my clean install I logged in recovery mode and typed:
sudo chown -R benjamin:benjamin /home/benjamin
sudo chmod 644 /home/benjamin/.dmrc
sudo chmod 644 /home/benjamin/.ICEauthority

No luck, any suggestions?

---

### Post by fearful on 2009-02-04
I really need help with this it's getting kind of annoying :S

---

### Post by Saul Perdomo on 2009-02-04
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=91455](http://ubuntuforums.org/showthread.php?t=91455)

(from page 4:
I have had this problem for a while...and finally tried to fix it. I was getting the message even though my .dmrc was set to 644 permission.

I changed the home folder permission to 700 (owner=rwx, and all others blank) and...

IT WORKED!!!

Now I can log on in peace. I hope this works for you!

djoefish)

---

### Post by fearful on 2009-02-04
YES!! thank you so much worked like a charm

clean logon finally:p

---

