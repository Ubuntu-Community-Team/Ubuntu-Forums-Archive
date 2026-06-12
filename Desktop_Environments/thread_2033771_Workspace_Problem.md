---
title: "Workspace Problem"
date: 2012-07-26
forum: Desktop Environments
---

### Post by merlinus on 2012-07-26
How can I get the gnome panels and menus to appear on additional workspaces?

I am using gnome classic with compiz, and all workspaces except the first come up with only my background graphic.

I have done a search of the forum for this issue, but none of the threads have been useful for me.

---

### Post by vexorian on 2012-07-26
There is a package called "gnome-tweak-tool" which has this option in its Gnome-shell section.

I haven't tested it since I only have one monitor.

Edit: Oh, completely sorry, I didn't notice you are using classic. I am afraid there is probably no way to tweak this. fallback is getting very little support :(

---

### Post by merlinus on 2012-07-26
Hi, and thanks for responding.  I have the gnome tweak tool, but cannot find anything there that will place the panels and menus on additional workspaces.  I also have only one monitor.

---

### Post by vexorian on 2012-07-26
Sorry, I constantly misread your question.

When I use classic gnome, I don't have this problem. I think you will have to disable the Desktop Wall and Desktop Cube (and any similar) extension from compiz. Then when there is only one workspace left, add the switcher to gnome-panel and change the number of workspaces. You won't have animations, but it shall work.

---

### Post by merlinus on 2012-07-26
Did not work.  The second workspace only shows the background graphic, and nothing else.  Thanks for trying!

---

### Post by vexorian on 2012-07-26
Ok, this beats me, because it is working in my setup. Does it work if you enter with (No effects)?

---

### Post by merlinus on 2012-07-26
No effects will change the desktop manager to Nautilus from compiz, which will not let me, for example, have all new windows open centered.  Kinda defeats the purpose...

---

### Post by vexorian on 2012-07-26
Well, I asked more to help isolate the problem (So we could have more clues as to what is the cause). After finding out you can switch to effects. Just want to know if the problem is because of fallback gnome or compiz or the combination.

The replacement of compiz in (no effects) mode is metacity. Nautilus is used in G3, unity, and fallback.

---

### Post by merlinus on 2012-07-26
Logging in with no effects did not make any difference.

---

### Post by merlinus on 2012-07-27
I can drag an open app to workspace 2, but it is the only window that appears -- still no panels, not even the workspace switcher.

The only recourse is Ctrl-Alt-Del.

---

### Post by merlinus on 2012-07-27
Update -- same problem exists on my laptop, running the same OS and configuration.

Can't anyone offer any suggestions or assistance???  Other than re-installing and having to re-configure every bloody thing -- arrrgghhhh!!!

---

### Post by vexorian on 2012-07-27
Try this:

1) do sudo apt-get install devilspie
2) Create this file in /home/yourname/.devilspie

(You might have to create the .devilspie folder)

gnopanel.ds
```

(if
    (contains (application_name) "Panel")

    (begin
        (pin)
    )
)


```


Press alt+F2 , then type "devilspie"

If this works, then add "devilspie" to the commands that are run at startup.


(devilspie is a background application that applies scripts to windows automatically.)

---

### Post by merlinus on 2012-07-27
It worked in terms of showing the panels and menus in other workspaces.  But when I open an application in any other workspace than #1, it will open in #1 and not the workspace I am in.

---

### Post by vexorian on 2012-07-28
It seems this is a lack of compatibility between compiz and devilspie.

But it seems compiz can do what devilspie does with the window rules extension. Right now, I don't know how to do it, but try checking it out, I guess that you can make a rule so that to make windows with application name that contains "Panel" stick in all workspaces.

[http://www.linuxquestions.org/questions/linux-software-2/devilspie-and-compiz-viewports-on-multiple-rows-860619/](http://www.linuxquestions.org/questions/linux-software-2/devilspie-and-compiz-viewports-on-multiple-rows-860619/)

---

### Post by vexorian on 2012-07-28
It seems this is a lack of compatibility between compiz and devilspie.

But it seems compiz can do what devilspie does with the window rules extension. Right now, I don't know how to do it, but try checking it out, I guess that you can make a rule so that to make windows with application name that contains "Panel" stick in all workspaces.

[http://www.linuxquestions.org/questions/linux-software-2/devilspie-and-compiz-viewports-on-multiple-rows-860619/](http://www.linuxquestions.org/questions/linux-software-2/devilspie-and-compiz-viewports-on-multiple-rows-860619/)

---

### Post by merlinus on 2012-07-28
Thanks for all your help -- much appreciated!

I played around with the various Windows Management settings in compiz, but was unable to figure out any way to make it work with additional workspaces.

---

### Post by vexorian on 2012-07-28
(Running out of ideas) Try (stick) instead of (pin) in that file. (You'll have to log out and log in again to restart devilspie).

---

### Post by merlinus on 2012-07-28
Changing the devilspie script to (stick) made the panels and menus not appear on the additional workspaces.

Also, changing the desktop manager to metacity rather than compiz still had apps opened in a different workspace appear on #1.

---

