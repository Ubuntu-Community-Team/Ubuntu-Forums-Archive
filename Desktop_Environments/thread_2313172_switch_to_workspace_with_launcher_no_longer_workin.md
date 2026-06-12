---
title: "switch to workspace with launcher no longer working with multiple desktops"
date: 2016-02-10
forum: Desktop Environments
---

### Post by mikee2 on 2016-02-10
[COLOR=#111111][FONT=Ubuntu]I used to be able to place different apps on different workspaces in Unity, and quickly navigate to any active app by clicking on its' icon in the launcher. This would navigate the screen display to whichever workspace that application was on.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After getting a secondary monitor hooked up this behavior is no longer present.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**For the record**: I am not talking about using the workspace switcher in the launcher itself. I am talking about the active apps in the launcher.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there a setting or restriction for this situation?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 14.04 64[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-02-11
I do not have a second monitor so I cannot test this. But I have noticed a problem and I have just worked out why it is happening. If an application's window overlaps the workplace edge then clicking the application icon in the launcher from the workspace alongside that edge will not switch workspaces.

For example, if a Libreoffice document is open in a top workspace but it is overlapping the bottom edge then when working in the bottom workspace I cannot switch back to Libreoffice by clicking its launcher icon. Resizing the Libreoffice application window solves the problem.

This may or may not relate to your problem.

Regards.

---

### Post by mikee2 on 2016-02-11
Thank you for your reply. I did a couple of tests myself and actually disabled the secondary monitor, but unfortunately got the same results. I am aware of the bug where the switcher will not switch to it when the window is partially inside another workspace. I have had that problem in the past, but this is still not the case presently. Even when my secondary monitor is disabled, and all applications are within their workspace, either maximized or floating, the switcher will still not go to the active application.

 I am getting a similar behaviour from the Window picker application in Compiz settings under --->Window Management--> Scale---> 'Initiate Window picker for all spaces'.  When initiated the window picker will show all active applications on all desktops, however if I choose an application that is not on the workspace that I am currently using, it will not switch the new workspace by going to the application that is selected.

This MAY have something to do with my current workaround for my secondary monitor problem (my audio receiver was being recognized as a secondary display, thus creating another desktop, and I only wanted Unity to see ONE display, not this virtual one)

My workaround was:

```

[COLOR=#111111][FONT=Ubuntu]xrandr --output NAME-OF-DISPLAY1 --rate 60 --mode 1920x1080 --fb 1920x1080 --panning 1920x1080* --output NAME-OF-DISPLAY2 --mode 1920x1080 --same-as NAME-OF-DISPLAY1[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]What this does is stacks your desktops on top of each other so that it appears & behaves as though there is only one desktop, however as I said, even disabling this secondary monitor does not change the behaviour of the workspace switching from the launcher. I'd still really like to figure this out. [/FONT][/COLOR]

---

### Post by mikee2 on 2016-02-12
resetting Unity and compiz did the job.

---

