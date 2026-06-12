---
title: "Removing shadow from titlebar,menus etc"
date: 2014-03-21
forum: Desktop Environments
---

### Post by haldardhruv on 2014-03-21
Somehow I probably screwed up my computer;) to show long shadows on title bars and drop down menus.Please tell me people how to remove it.I have uploaded the screenshot.The titlebar now appears black(which I don't wont it to be:()

---

### Post by bapoumba on 2014-03-21
It probably is the theme you are using.

---

### Post by haldardhruv on 2014-03-26
Nah. I switched to a different theme and it still shows. BTW I am using GreyBird.

---

### Post by bapoumba on 2014-03-26
Sorry to insist. did you try with with a standard theme (lubuntu-default for ex) and standard font (ubuntu) ?
GreyBird theme is not on the default list.

---

### Post by haldardhruv on 2014-03-27
Yep. I did that.(Anyway , GreyBird's a nice theme ;) )

---

### Post by bapoumba on 2014-03-28
Not ignoring, but not much to add. Does it happen with any application or only FF ?

---

### Post by haldardhruv on 2014-03-31
FF?:-kPlease explain what is it because I am new to this thing.

---

### Post by vasa1 on 2014-03-31
> **haldardhruv said:**
> FF?:-kPlease explain what is it because I am new to this thing.
FF = Fx = Firefox.

The question is whether you see these effects only with Firefox or with other applications as well.

I think you need to provide more information so that people can help you ...

What is your operating system?
What is its version?
Which desktop environment are you using?
Which window manager are you using?
If your problem is only with Firefox, what do you see with all extensions and themes/personas disabled?

I hope you understand that just saying you've done something isn't of much guidance.

But just from the single image, I'm guessing it's an issue with your window manager whatever that is. The window manager handles the appearance of the title bar. It also influences some dropdown menus. But you haven't given an image of that.

---

### Post by haldardhruv on 2014-03-31
With all of the applications:-|

---

### Post by haldardhruv on 2014-03-31
I just have an idea. Could it be because of Compton,a compositor that I once installed?If yes then how can I remove it?

---

### Post by vasa1 on 2014-03-31
> **haldardhruv said:**
> I just have an idea. Could it be because of Compton,a compositor that I once installed?If yes then how can I remove it?

Please answer the questions I asked :)

Also, make sure you use the ```
 tags to post the output of the following commands:

[CODE]env | grep XDG_CURRENT_DESKTOP
```

```
echo $DESKTOP_SESSION
```

```
lsb_release -a
```

Then, run 

```
sudo apt-get install wmctrl
```

and, after that, post the output of

```
wmctrl -m
```

---

### Post by vasa1 on 2014-03-31
Oh, and since you have installed Compton I wouldn't say, as you said, that you're new to these things ;)

Compton isn't is the standard Software Center. And it should be obvious to you at least whether these shadows started appearing before or after you installed Compton. In which case you have your answer!



> Compton may be manually enabled or disabled at any time during a session, or autostarted as a background (Daemon) process for sessions. There are also several optional arguments that may be used to tweak the compositing effects provided. These include:

    -b: Run as a background (Daemon) process for a session (e.g. when autostarting for a window manager such as Openbox)
    -c: Enable shadow effects
    -C: Disable shadow effects on panels and docks
    -G: Disable shadow effects for application windows and drag-and-drop objects
    --config: Use a specified configuration file

Many more options are availble, including to set timing, displays to be managed, and the opacity of menus, window borders, and inactive application menus. See the Compton Man Page for further information. from [https://wiki.archlinux.org/index.php/Compton](https://wiki.archlinux.org/index.php/Compton)

---

### Post by haldardhruv on 2014-03-31
That's it ! Solved!Thanx vasa1:guitar:

[COLOR=#000000][FONT=sans-serif]To disable all shadowing effects from the [Daemon]("https://wiki.archlinux.org/index.php/Daemon") process, the -C and -G arguments must again be added:[/FONT][/COLOR]
compton -CGb

---

### Post by haldardhruv on 2014-03-31
I found 1 more link on [https://github.com/chjj/compton/wiki/faq](https://github.com/chjj/compton/wiki/faq)
[h=2]1. Why is compton painting a shadow around my conky window?[/h][COLOR=#333333][FONT=Helvetica]You have to set own_window_type desktop in .conkyrc, or use --shadow-exclude to disable shadows on this specific window (assuming you didn&#8217;t change the default class of conky&#8217;s window, --shadow-exclude 'g:e:Conky'). The former solution is much easier and will make your conky cooperate better with other programs.

conky&#8217;s own_window_hints undecorated has no effect on compton, because we cannot just avoid painting shadows on all undecorated windows.

[/FONT][/COLOR]

---

### Post by bapoumba on 2014-03-31
Glad to see you got it to work :)
Please mark your thread as solved :[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads), thanks.

---

