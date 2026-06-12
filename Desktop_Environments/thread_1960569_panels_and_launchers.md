---
title: "panels and launchers"
date: 2012-04-17
forum: Desktop Environments
---

### Post by DanBender on 2012-04-17
I've installed Qimo on a laptop for my 2-year-old and am trying to get it configured so it's easy for him to use.

I've got the xfce panel that launches applications *mostly* set up the way I want, but I am running into one issue. I installed a set of games which each one is launched from its own shortcut (It's actually Windows programs running in Wine); it's not like the GCompris suite Child's Play that are a bunch of sub-programs that launch from a single main program.

In the panel, I can add "launchers" to start all these programs ("with optional menu"). However, the only way I can seem to set it up is there's one "main" button assigned to one of them, and the rest accessed with a small button right next to it, like this:
```

                       [     ]
                       [ 123 ]
                       [     ]
                       -------
                       [COLOR=Black][     ]
                       [/COLOR][COLOR=Black][SHAPE]
                       [/COLOR][COLOR=Black][     ][/COLOR]
                       -------
                       [     ]
                       [THINK]
                       [     ]
   ------------------------------------
   [COLOR=Silver] [     ][/COLOR] [COLOR=Silver][     ][/COLOR] [     ][s] [COLOR=Silver][     ][/COLOR]
... [COLOR=Silver][  1  ][/COLOR] [COLOR=Silver][  2  ][/COLOR] [ ABC ][u] [COLOR=Silver][  3  ][/COLOR] ...
    [COLOR=Silver][     ][/COLOR] [COLOR=Silver][     ][/COLOR] [     ][b] [COLOR=Silver][     ][/COLOR] 
```where "1", "2", and "3" are other "launchers" or buttons in the panel like GCompris, "watch cat videos", log out, other stuff; and are the only items in each of those "launchers." "ABC" is the first item in that particular "launcher."

What I WANT to have it be like is:
```

                    [     ]
                    [ ABC ]
                    [     ]
                    -------
                    [     ]
                    [ 123 ]
                    [     ]
                    -------
                    [COLOR=Black][     ]
                    [/COLOR][COLOR=Black][SHAPE]
                    [/COLOR][COLOR=Black][     ][/COLOR]
                    -------
                    [     ]
                    [THINK]
                    [     ]
   ---------------------------------
   [COLOR=Silver] [     ][/COLOR] [COLOR=Silver][     ][/COLOR] [     ] [COLOR=Silver][     ][/COLOR]
... [COLOR=Silver][  1  ][/COLOR] [COLOR=Silver][  2  ][/COLOR] [GAMES] [COLOR=Silver][  3  ][/COLOR] ...
    [COLOR=Silver][     ][/COLOR] [COLOR=Silver][     ][/COLOR] [     ] [COLOR=Silver][     ][/COLOR] 
```where you click on the main button and it pops up the menu, rather than the little button right next to it. The boy's only 2 1/2; asking him to reliably click a little tiny thin button is asking a bit much.

I haven't found much information on how the "launcher" plugin is configured; it's all been trial-and-error so far. It's not obvious if there's a way to configure it to always throw the menu up, or if there's another plugin that would do that. The nice thing about that particular panel system is the ability to use BIG BUTTONS.

I've tried the "application menu" plugin as well, but it seems to be a clone of whatever is in the main XFCE application menu, and I'm not finding any information about whether the menu can be something different. I do NOT want him to have access to the main applications menu.

I'm not ruling out other panel/launcher systems; I've tried loading several from Synaptic, but have had only limited success in getting them to even show in the XFCE environment, let alone be configurable. I'm also not averse to a new-window-style launcher that lists all the games once I click it on the panel, as long as it can use BIG BUTTONS and it has to go away once it launches the chosen program. Like I said, he's only 2 1/2 so he doesn't get the idea of a "back" or a "close window" button yet.

Does anyone have any suggestions for this?

Thank you for your help.

---

### Post by Toz on 2012-04-17
What version of xfce are you using? On 4.8, in the same dialog where you create the multiple launchers, on the Advanced tab, you can set the Arrow Button Position. If you set it to "Inside Button", then whenever you click the launcher, instead of launching the default launcher, it opens a menu that lists all of the launchers listed that you can select from.

As a suggestion to create the second layout (Games->Think->Shape->123), in conjunction with the Inside Button setting, you could create a default blank (non-executable) entry called Games that could act as the main launcher (just set the command to /bin/false so that nothing launches). Then add the other games into the launcher.

Here are some screen captures to illustrate:

---

### Post by DanBender on 2012-04-20
Thank you, Toz! That's not exactly what I want, but it's close enough. I did that but set it to show the last item used in the launcher, so there isn't any unused entries that could cause confusion.

---

