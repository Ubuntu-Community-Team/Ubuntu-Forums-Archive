---
title: "Pidgin, Feisty, gtkrc-2.0 and bindings"
date: 2007-07-08
forum: Desktop Environments
---

### Post by IndieRockSteve on 2007-07-08
I just upgraded my laptop to Feisty and noticed my GAIM keybindings no longer worked. 

I took the "opportunity" to install Pidgin from [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/) and update the gtkrc-2.0 binding info to what the pidgin faq shows, but still no go. 

anyone know why the binding won't work after I restart GAIM/Pidgin?

in .gtkrc-2.0 I have:
include "/home/myusername/.gtkrc-2.0.mine"

and in .gtkrc-2.0.mine I have,
#############################
#key bindings
#############################

# Controls the keybindings that gtk uses for text entry/editing/etc
# The "emacs" theme turns on things like:
# ctrl-a == move to beginning of line, ctrl-e == move to end of line, etc.
gtk-key-theme-name = "Emacs"

#to let you edit your pidgin key bindings
gtk-can-change-accels = 1

# In Gaim 2.0.0 and later, you can set custom keybindings in your theme.  Here
# is an example to follow

binding "my-bindings"
{
# enter inserts a newline
        bind "Return" { "insert-at-cursor" ("\n") }
# ctrl-s sends message
        bind "<ctrl>Return" { "message_send" () }
# shift-f1 toggles bold
        bind "<shft>F1" { "format_function_toggle" (1) }
# alt-f2 toggles italic
        bind "<alt>F2" { "format_function_toggle" (2) }
# Ctrl-alt-shift-f3 toggles underline
        bind "<ctrl><alt><shift>F3" { "format_function_toggle" (4) }
# Ctrl-f1 resets the formatting
        bind "<ctrl>F1" { "format_function_clear" () }
}

widget "*pidgin_conv_entry" binding "my-bindings"

---

### Post by Gremlinzzz on 2007-07-08
Don't know but the comments here seem to have problems too.think i'll wait till the bugs are out.
[http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

---

### Post by IndieRockSteve on 2007-07-08
yea, except the problem also occurs with gaim from Ubuntu's repository so it's got to be something wrong beyond gaim/pidgin and more likely with Feisty's handling of the gtkrc-2.0.

It's too bad they decided to make users have to edit gtkrc-2.0 to do simple keybinding changes instead of how the old gaim had it as a GUI option....

---

### Post by fjgaude on 2007-07-08
AFAIK, Pidgin is still not ported to Feisty. It's gonna be in Gusty.

frank

---

### Post by IndieRockSteve on 2007-07-08
wow, this place is good at ignoring my question.

---

### Post by runokiab on 2007-10-25
The following in ~/.gtkrc-2.0 works for me. 
```
binding "my-bindings"
{
# enter inserts a newline
bind "Return" { "insert-at-cursor" ("\n") }
# ctrl-s sends message
bind "<ctrl>s" { "message_send" () }
# shift-f1 toggles bold
bind "<shft>F1" { "format_toggle" (1) }
# alt-f2 toggles italic
bind "<alt>F2" { "format_toggle" (2) }
# Ctrl-alt-shift-f3 toggles underline
bind "<ctrl><alt><shift>F3" { "format_toggle" (4) }
}
widget "*pidgin_conv_entry" binding "my-bindings"

gtk-key-theme-name = "ctrl-return"

    gtk-can-change-accels = 1

    binding "my-bindings" {

    bind "<ctrl>Return" { "message_send" () }

    bind "<ctrl>KP_Enter" { "message_send" () }

    bind "Return" { "insert-at-cursor" ("\n") }

    bind "KP_Enter" { "insert-at-cursor" ("\n") }

    }

    widget "*pidgin_conv_entry" binding "pidgin-bindings"

```

It's partly from the example config that can be found on [http://developer.pidgin.im/viewmtn/revision/file/62fa92a34f063b3edb8402fcc5e302f1ad9b4baa/doc/gtkrc-2.0]("http://developer.pidgin.im/viewmtn/revision/file/62fa92a34f063b3edb8402fcc5e302f1ad9b4baa/doc/gtkrc-2.0")
I don't really know which part actually makes it happen, and I don't have to time to figure it out right now, but maybe it's a starting point for others.

---

