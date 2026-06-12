---
title: "How to change or disable the F11 key?"
date: 2010-09-16
forum: Desktop Environments
---

### Post by tim042849 on 2010-09-16
Using ubuntu 10.04 32-bit.
I would like to disable or remap (preferably) the F11 key action which
toggles full-screen mode. I can find the keymapping under
```
System->Preferences->Keyboard Shortcuts->Window Management->Toggle Fullscreen Mode
```
Disabling the feature has **no** effect. I can add a shortcut
say **mod4-F11** and that shortcut then becomes effective, but
the F11 action remains. That is quite annoying!

I hope that someone can tell me how to fix this.
thanks
tim

---

### Post by tim042849 on 2010-09-17
Kind of disappointing that I have no replies about this
problem. Perhaps if someone else can replicate - this 
should be submitted as a bug?

---

### Post by scorchgeek on 2010-09-17
Well, turning off that option will indeed not turn off that shortcut in *other programs*, say, Firefox. However, if you remap the F11 key to something else using the Keyboard Shortcuts window, GNOME will capture your keystroke before it reaches Firefox (or any other program), and full-screen will not take effect.

If you wanted to disable it completely, I suppose you could write a shell script that did nothing and set that as the action.

(Honestly, I don't even know what that "full screen" option in that dialog box does--perhaps someone could enlighten me?)

---

### Post by tim042849 on 2010-09-17
Thank you for your reply scorchgeek. I believe that my experience is
different from what you describe above. Let's take another default
key mapping for ubuntu:
1)Alt-Tab. Alt-tab is used in Midnight Commander. Thus I have remapped
**Move between windows using a popup menu**
to Ctrl-F10. Works fine in both gnome applications using
X and console apps like MC, Mutt etc.
Yet, with keymapping disabled for **toggle fullscreen mode**,
F11 will still toggle fullscreen mode in any console application. And
(as far as I know) any other X app that does not explicitly remap
F11. This is different from any other keymapping.

I **have** successfully remapped F11 in gvim - which is an X
application - to be distinguished from vi or vim.

And as for your last sentence: All **toggle fullscreen mode** does on
my desktop is switch of the panel(s).

regards
tim

---

### Post by scorchgeek on 2010-09-17
> Yet, with keymapping disabled for toggle fullscreen mode,
F11 will still toggle fullscreen mode in any console application. And
(as far as I know) any other X app that does not explicitly remap
F11. This is different from any other keymapping.
I'm not exactly sure what "This is different from any other keymapping" means. If you could clarify this, that would be great.

As I said before, but obviously not clearly enough (sorry), the "toggle fullscreen" option has nothing to do with the full-screen option in any programs at all, only GNOME itself (you said it makes your panels disappear). If you are wanting to disable the full-screen function for a particular program, you need to either configure the window manager to capture that keystroke and not send it on to the program, as I described in my last post, or change that setting in the program itself, if that's an option. In the case of GNOME Terminal, you can choose Edit-->Keyboard Shortcuts, scroll all the way to the bottom, and disable or remap the F11 key for GNOME Terminal.

Making the setting in the main System-->Preferences-->Keyboard Shortcuts will indeed have no effect, as it is not a database all programs take their settings from. It works like this: when you type F11, the keyboard will send the F11 keystroke to GNOME. If F11 is assigned, GNOME will run that action. If it is not, F11 will be passed to the application with the focus, in this case making your terminal go full-screen. In other words, disabling the shortcut simply causes GNOME to send on your keystroke, rather than simply ignore it.

The difference between this and Alt-Tab is that Alt-Tab is being accepted and acted on by the window manager, rather than an application.

I hope this clears up any confusion.

---

### Post by tim042849 on 2010-09-18
Yes, you have cleared up the confusion. I unmapped F11 in gnome-terminal.
I'm beginning to understand that F11 is a common mapping in different application, just as F1 is. I appreciate the help.
cheers
tim

---

