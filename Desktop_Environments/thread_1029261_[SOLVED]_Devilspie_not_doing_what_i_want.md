---
title: "[SOLVED] Devilspie not doing what i want"
date: 2009-01-03
forum: Desktop Environments
---

### Post by nlz on 2009-01-03
I've got devilspie installed from the repo, and i've made the folder ~/.devilspie 
In there, there are 4 files; 1.ds, 2.ds, 3.ds and 4.ds

But when i start devilspie and start one of the apps, nothing starts on another workspace. I've tried it with compiz on and off. What can it be?
devilspie shows no error messages when it starts. Please advice.

1.ds:
```
(if
    (is (application_name) "firefox-bin")
    (begin
       (set_workspace 2)
       (maximize)
    )
)


```2.ds:
```
(if
    (is (application_name) "firefox")
    (begin
       (set_workspace 3)
       (maximize)
    )
)

```3.ds:
```
(if
    (is (application_name) "thunderbird")
    (begin
       (set_workspace 3)
       (maximize)
    )
)

```4.ds:
```
(if
    (is (application_name) "songbird")
    (begin
       (set_workspace 4)
       (maximize)
    )
)
```

---

### Post by Jose Catre-Vandis on 2009-01-03
You may have some syntax problems with you window/application names.

check these by opening up a terminal, then open up each program.
in the terminal type xprop and then press return. Your pointer will turn into a cross. Click on one of your application windows and a pile of stuff will fly by in your terminal. You are interested in WM CLASS (String).

So for firefox you will see "WM_CLASS(STRING) = "Navigator", "Firefox""

therefore you need to put Firefox in your .ds file, not firefox.

You may have trouble with your second firexo entry as devilspie would need the complete name of the window to do what you want


All that said, try out the window matching features in compiz, they work pretty well and should also achieve what you want to do:

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by nlz on 2009-01-03
Did what you said, thanks for that. but it's still not working. I've got one problem and one question:
1.
I get these errors when i start devilspie, although I have 4 workspaces
```

trotski@labda:~$ devilspie

** (devilspie:2235): WARNING **: Workspace number 3 does not exist

(devilspie:2235): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

** (devilspie:2235): WARNING **: Workspace number 3 does not exist

(devilspie:2235): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

** (devilspie:2235): WARNING **: Workspace number 3 does not exist

(devilspie:2235): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
```

2. Should I take the first or the second outcome after WM_CLASS(STRING) 

For instance here:

```
WM_CLASS(STRING) = "transmission", "Transmission"
```

or are they both OK?

---

### Post by Jose Catre-Vandis on 2009-01-04
1. Your workspaces are probably generated through compiz

(I would still recommend you try to do what you need to do through compiz, if you want to use compiz, that is)

If you have compiz turned off then the workspaces won't be there! :)

2. The second entry with the capital "T"

---

### Post by mtbsoft on 2009-01-04
Try replacing "set_workspace" with "set_viewport" - workspaces don't work for me but viewports do just fine.

I also found a gui called gDevilspie which can help setting these up - Google for it.

---

### Post by nlz on 2009-01-05
whoot! with the GIU (which can be downloaded here: [http://code.google.com/p/gdevilspie/wiki/gDevilspie](http://code.google.com/p/gdevilspie/wiki/gDevilspie) )and compiz switched off it works!

Now i'll try to start everything up before compiz, hopefully it works. i'll keep you informed. thanks.

---

### Post by reader4 on 2009-01-07
I use the method described by mtbsoft with compiz-fusion: "set_viewport" works, "set_workspace" does not.

---

### Post by nlz on 2009-01-09
OK, I'm starting to feel darn stupid.

So with compiz:

1. I start ccsm
2. I go to Place Windows (under window management)
3. I go to the Fixed window placement tab
4. I go to Windows with fixed viewport
5. Press new
6. Grab a window
7. Set ANY setting on the X viewport of Y viewport setting.

Nothing happens! What X viewport setting are for workspace 1,2,3 or 4?

Am I missing something?[IMG]http://radioinethiopia.org/paginas/images/window.png[/IMG]

---

### Post by nlz on 2009-01-09
I found it out! the x viewport value is the workspace. To if you want the 3rd workspace, just enter 3.
Thanks to the guys at the #compiz-fusion channel.

---

