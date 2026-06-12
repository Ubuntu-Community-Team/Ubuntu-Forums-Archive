---
title: "Panel closes itself with error message"
date: 2009-11-25
forum: Desktop Environments
---

### Post by hypergeek14 on 2009-11-25
Hello.  

I'm using _Xubuntu 9.10_ on a _Lenovo Ideapad S10e_ netbook.  While I was installing the _Broadcom STA_ driver for my _Broadcom 802.11g BCM 4312_, the panel disappeared.  I rebooted and it still wasn't there.  

I punched in *xfce4-panel* and the panel appeared (wireless is finally working, thank god).  The terminal spit out the following output: 
```

keith@keith-netbook:~/Desktop$ xfce4-panel

(xfce4-mixer-plugin:1854): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1854): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1854): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed
```

When I close the terminal, the panel closes.  And if I remove the Mixer from the panel, it adds this to the output and solves nothing:  

```
(xfce4-mixer-plugin:1854): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed
```

I miss my panel.  How can I get it back?

---

### Post by hypergeek14 on 2009-11-25
I probably should have tried to figure it out myself for a bit before rashly asking the forums!  The solution was to punch in *xfce4-panel* in the run dialog you get from *ALT+F2* instead of putting it in the terminal.  

Thanks anyway!  Hope that helps people with a similar problem in the future.

---

### Post by fancypiper on 2009-11-25
You could also issue the command with the nohup option or run it in the background with command &

Then you can close the terminal and the panel will stay open.

---

