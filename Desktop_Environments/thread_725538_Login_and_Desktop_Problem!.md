---
title: "Login and Desktop Problem!"
date: 2008-03-15
forum: Desktop Environments
---

### Post by delsydebothom on 2008-03-15
I was *trying* to install the ePSXe using the directions at this link [http://ubuntuforums.org/showthread.php?t](http://ubuntuforums.org/showthread.php?t)...

I don't know what happened, but now I can't log in to my profile. When I try to log in, I get this message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session from being saved. File should be owned by the user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."

Before it kicks me out, there is another dialog box that comes up. It says:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem.

[] View details (~/xsession-errors file)

(process: 6049) GTK-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead.

For further details, see: [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+

(Process 6053) [At this point, it repeats the same message, and then tells me it can't create any of my main folders--the ones that would be under the "places" tab]

(x-session-manager: 6046): libgnome fs- WARNING **: unable to create ~/.gnome2 directory: Permission denied. Could not create per-user gnome configuration directory[lists directory]: permission denied."

Is there anything I can do??

---

### Post by unutbu on 2008-03-15
Press Ctrl-Alt-F2. This will take you to a text console. Log in.
At the prompt, type
```

cd /home
sudo chown -R <username>:<username> <username>

```

Replace <username> with your user name. Log out by typing 'exit'.

Now flip back to the graphical login window by typing Ctrl-Alt-F7. Try logging in.
If it does not work, go back to the text console. Log in at the text console.
This time, type
```

chmod -R 755 <username>

```

Beware that the chmod command will change the permission of every single file in your home account to become readable and writable for you, and readable for everyone else. 
If you wish to make your account unreadable to everyone else, replace 755 with 700.

Again log out of the text console, flip back to the graphical login window. Hopefully, you should be able to log in now.

---

### Post by delsydebothom on 2008-03-16
Thank you! Your second suggestion fixed everything right up!

---

### Post by unutbu on 2008-03-16
Yay!!!! :popcorn:

---

