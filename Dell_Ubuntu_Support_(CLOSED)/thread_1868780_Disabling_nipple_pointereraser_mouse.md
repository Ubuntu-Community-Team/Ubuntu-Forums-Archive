---
title: "Disabling nipple pointer/eraser mouse?"
date: 2011-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Boogerhead on 2011-10-24
Kind folks,

I've bludgeoned back together a beaten-up Dell D600 laptop for my girl to use.

Problem is, the nipple pointer/pencil eraser mouse keeps drifting, and often takes control of the machine away for minutes at a time. I'd like to disable the thing entirely, but can't figure out how.

We're on 11.10 as of this afternoon.

Earlier threads told me to edit xorg.conf, which no longer exists, or create it with Xorg --configure, which doesn't work when X is running. Then I'm supposed to edit a section for the nipple pointer for SendCoreEvents to False, but I don't have a file to edit, nor anything to mimic.

Where should I go here?

---

### Post by ##Villain on 2011-10-25
> **Boogerhead said:**
> Kind folks,

I've bludgeoned back together a beaten-up Dell D600 laptop for my girl to use.

Problem is, the nipple pointer/pencil eraser mouse keeps drifting, and often takes control of the machine away for minutes at a time. I'd like to disable the thing entirely, but can't figure out how.

We're on 11.10 as of this afternoon.

Earlier threads told me to edit xorg.conf, which no longer exists, or create it with Xorg --configure, which doesn't work when X is running. Then I'm supposed to edit a section for the nipple pointer for SendCoreEvents to False, but I don't have a file to edit, nor anything to mimic.

Where should I go here?

Okay I had the same EXACT problem, so stay with me. First, go into terminal and type "gconf-editor" (without quotes). Now click **[color=green]app->metacity-> keyboard commands**[/color].

In command 1 edit the key and add

```
xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0
```

That code DISABLES the touchpad and pointer stick.

In command 10 or any (doesn't matter) add:

```
xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1
```

That command ENABLES the touchpad & pointer stick.

After you have done this, go to [color=green]**global keybinds[/color]**. Go to **run_command_1** and add a shortcut (for ex. <super>e which makes it so the key with the windows sign plus the letter e enables the pad and pointer stick). You must make different shortcut keys. I have mine as <super>d for disable and <super>e for enabling. After you have doe that, then just try the shortcut.

---

