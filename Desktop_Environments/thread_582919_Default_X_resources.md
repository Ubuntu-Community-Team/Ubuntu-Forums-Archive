---
title: "Default X resources"
date: 2007-10-20
forum: Desktop Environments
---

### Post by jbro on 2007-10-20
I've just installed Gutsy Gibbon and so far everything is pretty good. Everything works and things are pretty smooth. I do have one question about the X resources that Gutsy sets up. I have a very simple ~/.Xresources file with some color information in it. However, when I start emacs, it doesn't use the colors set in my .Xresources file. I did "xrdb -query" and I get the following:

```

Emacs*Background:       #ffffff
Emacs*Dialog*background:        #efebe7
Emacs*Dialog*foreground:        #101010
Emacs*Foreground:       #000000
Emacs*XlwScrollBar.Background:  #efebe7
Emacs*XlwScrollBar.Foreground:  #101010
Emacs*backgroundToolBarColor:   #efebe7
Emacs*bottomToolBarShadowColor: #efebe7
Emacs*menubar*background:       #efebe7
Emacs*menubar*foreground:       #101010
Emacs*popup*Background: #efebe7
Emacs*popup*Foreground: #101010
Emacs*topToolBarShadowColor:    #efebe7
Emacs.default.attributeBackground:      #ffffff
Emacs.default.attributeForeground:      #000000
Emacs.menuBar:  off
Emacs.mode-line.attributeForeground:    #101010
Emacs.pane.menubar.font:        -xos4-terminus-bold-r-*-*-*-140-*-*-*-*-iso10646-1
Emacs.pane.menubar.margin:      1
Emacs.pane.menubar.shadowThickness:     1
Emacs.scroll-bar.attributeBackground:   #efebe7
Emacs.scroll-bar.attributeForeground:   #101010
Emacs.tool-bar.attributeBackground:     #efebe7
Emacs.tool-bar.attributeForeground:     #101010
Emacs.toolBar:  off
Emacs.verticalScrollBars:       off

```

About three or four of these resources are set in my .Xresources file. I would like to know where the rest are. I checked the X startup as much as I could and it seems the global Xresources file is in /etc/X11/Xresources. I checked that file and it does not have any of the resources defined in the listing above in it.

So, the question is from where is Gutsy loading all of these resources? I'd like to at least eliminate the color information so my colors work.

Thanks and regards,
jbro

---

