---
title: "applications open in the wrong desktop"
date: 2007-06-13
forum: Desktop Environments
---

### Post by vadania on 2007-06-13
I would like applications I launch in a desktop - say desktop 3- to stay there and not open windows and popups in any desktop I have selected right now.
For example: I start Eclipse (or Psi, a Jabber client) on desktop 3, and then I don't wait for the application to load, immediately switch to desktop 4 doing something else (for example, web browsing) while Eclipse is loading.
What do I get? Eclipse loads in desktop 4, and I have to manually move it to dektop 3!
Is it that these are both Java apps?

---

### Post by Soarer on 2007-06-13
I don't think it has anything to do with them being Java apps. The application will load in the desktop you have selected when it draws it's window. At least, mine always do. It CAN be annoying, so I;d be interested to know if there's anyway to stop it.

---

### Post by gfixler on 2007-06-13
It doesn't have to do with Java. Any app will do that. To take powerful control over your apps' windows when they first open, have a look at Devil's Pie.

[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

It's a utility you can launch whenever (e.g. at startup (System->Preferences->Sessions), and then it watches for any new window to be created, whereupon it checks your ~/.devilspie directory's *.ds files for rules that might pertain to that window, and modifies it as you've specified.

The rules are styled like Lisp code (not sure if it's actually Lisp underneath), and you make one .ds file per rule. To give you a good example, I have one for Amarok in ~/.devilspie/amarok.ds that contains this line:

(if (is (application_name) "Amarok") (begin (set_workspace 5) (geometry "+10+10") maximize))

If the application window is entitled "Amarok," it moves it to workspace 5, then 10 pixels in and down from the top left edge of my left monitor, and then maximizes it there. I have 6 of these files. Here's another one for Firefox, which I have in ~/.devilspie/firefox.ds:

(if (is (application_name) "Firefox") (begin (set_workspace 1) (geometry "+1300+10")  maximize))

Same deal, but +1300 gets it over to my right monitor, on a different desktop. Then it's maximized to my right monitor. You can also fullscreen, in lieu of maximise which I have for some shell window placements, as that makes them borderless - wall-to-wall shell, instead of just screen-sized.

Extra cool has been adding a script to a folder in my path that will launch my 6 most used apps, which are then all placed properly by Devil's Pie. I then put a call to that script on a button on my panel, so when I get home at night, and want to fire up all my usuals, I just click that, and wait about 20 seconds for them all to finish loading, and moving around. I even put a call to that script in my session startup, so I'd just turn the machine on, log in, and go take care of a chore while it finished loading, and opening/placing everything for me, and return to a machine ready to work :)

You can also make a .ds file that just says (debug) - parentheses included, and it'll print out the information in the shell from which you started Devil's Pie any time you open a window, and then you can use that info in your .ds scripts, as there are other things besides application_name that you can have it search for.

Right now I need to change the Firefox thing, because every window it pops up, including OK dialogs, and the download progress window all try to maximize to monitor 2 on desktop 1, too. I should key off something more appropriate. Also, I removed the session startup launcher, because sometimes I didn't want them all open after booting up, and it was annoying waiting for them all, then going desktop-by-desktop, shutting them all down. I'm back to just using my panel button.

Good luck.

---

### Post by jimcooncat on 2007-06-14
> **gfixler said:**
> ... Also, I removed the session startup launcher, because sometimes I didn't want them all open after booting up, and it was annoying waiting for them all, then going desktop-by-desktop, shutting them all down. I'm back to just using my panel button.

Having a default set of programs boot up *is* very cool. I think for your usage, you could reimplement this having it start from a script like (this is no doubt full of bugs, just an example):

```
# set up a zenity killer in the background, 10 second timeout
sleep 10 && killall zenity &

# display a question to abort autoloading of programs
zenity  --question --title "Alert"   --text  "Don't run default programs?"

retval=$?

case $retval in
    0)
        exit;;
    1)
        sleep 0;;
esac

devilspie *your arguments*
```

Feedback appreciated!

---

### Post by gfixler on 2007-06-15
Cool. I don't understand much of that, so it looks like I've got some new things to learn.

Thanks!

---

### Post by jimcooncat on 2007-06-16
Better comments for more explanation
```

# set up a zenity killer in the background, 10 second timeout
# start a background program -- & at the end
# sleeps for 10 seconds
# && means "if previous command (sleep 10) worked well, do next command"
# killall zenity means kills zenity, that is, destroy the dialog box
sleep 10 && killall zenity &

# display a question to abort autoloading of programs
# pops up a dialog box. If you press OK, the program gets a zero. Otherwise, a one.
zenity  --question --title "Alert"   --text  "Don't run default programs?"

# assign the zenity output (either a zero or one) to retval (a variable, just a name 
#    we give to a storage place for the one or zero)
retval=$?

# inspect the variable, and do something depending on its value
case $retval in
    0)
        # abort this program
        exit;;
    1)
        # dont do anything
        sleep 0;;
# this stops the case command that inspects the variable
esac

# run your programs with all kinds of devilspie control
devilspie *your arguments*
```

So when you log in, a dialog box pops up asking if you want to stop loading your programs. If you're right there to press OK, stuff won't load and you can get on with business immediately.

If you press Cancel or close the dialog box, your default programs start loading.

Or if you just take off to get a cup of coffee, the dialog box gets killed after ten seconds and your default programs load. By the time you get back, it's all set to go with your favorite setup.

At least that's the way I envision how this is supposed to work. It probably doesn't work correctly, I didn't take proper time to look up and test each command the way I should have.

---

### Post by vadania on 2007-08-10
Where should I place that script? 
in my .bashrc file?
If not, In what file exactly should I put it?

In System> Preferences> Session there is a list of applications that open with every new session.
Could I put my script there? But then, how do I know that applications will not open Before running my script?

Thanks,

---

