---
title: "cannot change keyboard layout, have to use my mouse"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ianikeev on 2005-10-24
Hello everyone,

I decided to try KDE under ubuntu, all's just fine, but I cannot make the keyboard layout switch from English to Russian and vice versa. I can surely do it by clicking the icon, but it's not too entertaining. I used KControl to set up keyboard switching and set ctrl+shift as the trigger. Any ideas? Everything's perfect in GNOME. :confused: 

After sone tweaking I still haven't had any success with automated keyboard layout switching in KDE under Ubuntu. I remember to have had similar problems with different distros with recent KDE versions (SuSE fo example). It drove me to GNOME. I'd like to give KDE another try, but again, switching keyboard layouts with my mouse is not an option, as I write a lot in both English and Russian. :(

---

### Post by ianikeev on 2005-10-24
Some extra info:

for US layout Kcontrol shows the following line:
setxkbmap -model sven -layout us -variant rus

for Russian layout:
setxkbmap -model sven -layout ru -variant winkeys

and in the options section:
setxkbmap -option compose:rwin,grp_led:scroll,altwin:left_meta_win,grp:ctrl_shift_toggle,eurosign:e

The keyboard is correctly set as SVEN 2500 Ergonomic.

So why can't I change the layout by pressing ctrl+shift?

---

### Post by red_plague on 2005-10-24
So, i tried to make a keyboard switch between 2 layouts, and i tried to put Ctrl+Shift as the modifier key, Well, the control center didn't let me pt only Ctrl+Shift, it insisted on putting a letter also, so i put Alt+z and it worked.
 It makes sense, since Ctrl+Shift+a (for instance): you have to press first Ctrl then Shift, and at this point your layout would change ;) (i think). So you have to set something like Ctrl+m or Alt+p, or Ctrl+Alt+q to work without problems with keyboard switching. (Avoid ctrl+a, ctrl+c, ctrl+v, ctrl+s, ctrl+w, and other shortcuts like this)

---

### Post by ianikeev on 2005-10-24
But why it works under GNOME? (and Windows, for that matter) :confused: 

It´s confusing, as I have to use gnome, while kde suits my needs better. Any KDE gurus to help?

---

### Post by grinias on 2005-10-26
Yes, it works in gnome. I have the same problem in english-greek layout change. The exact problem is that my ctrl keys are not recognized by Layout Selector when i am in greek mode and thusfore I can't change from greek to english.

---

### Post by grinias on 2005-10-30
Finally, i managed to solve the problem.

You have to do
```
 
sudo vi /etc/X11/xkb/rules/xfree86

```

find the lines in /etc/X11/xkb/rules/xfree86 
```

// If you want non-latin layouts implicitly include the en_US layout
// uncomment lines below
//! $nonlatin = am ara ben bg by deva ge gr guj guru il \
//             ir iku kan lao mk mm mal ori ru scc syr tel th\
//              tj tam ua


```

and uncomment the three last lines as it is suggested by the first two of them
to get

```

// If you want non-latin layouts implicitly include the en_US layout
// uncomment lines below
! $nonlatin = am ara ben bg by deva ge gr guj guru il \
             ir iku kan lao mk mm mal ori ru scc syr tel th\
              tj tam ua


```

Then save the file, restart X (Ctrl-Alt-Backspace) and  (hopefully) enjoy!:smile:

---

### Post by atenlaugh on 2006-07-12
None of these things work for me, under Dapper.

It's ridiculous that this just won't work in Kubuntu...

---

### Post by grinias on 2006-07-14
Are you sure? Because it worked for me in Kubuntu Dapper too. 
Have you done the right choises under 

KMenu->System Settings->Regional & Accessibility

in Keyboard layout? And what is the language you are interested about?

---

