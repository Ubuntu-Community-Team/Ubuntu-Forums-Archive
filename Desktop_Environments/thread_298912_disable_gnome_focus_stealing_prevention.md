---
title: "disable gnome focus stealing prevention"
date: 2006-11-13
forum: Desktop Environments
---

### Post by kruschev on 2006-11-13
I would like to disable focus stealing prevention so that windows can pop themselves up as they like.  When I use matlab for example i want to type "edit" and have the editor pop up.  Tabbing over to the editor is annoying. I saw a similar question here:

[http://gnomesupport.org/forums/viewtopic.php?t=11560](http://gnomesupport.org/forums/viewtopic.php?t=11560)

but without a solution. Can anyone help?  It ought to be made an option in gnome, because although good for most people this "feature" really annoys me. If I can't solve it I guess I'll switch back to kde although gnome is otherwise very nice.

---

### Post by dpm on 2006-11-13
AFAIK you cannot disable it, unless there is some key I don't know of in gconf to do it.

IIRC, focus stealing prevention is as good as its implementation by the application which is using it, so it might not be an issue with metacity but with Matlab itself.

---

### Post by localuser on 2006-11-13
> **kruschev said:**
> I would like to disable focus stealing prevention so that windows can pop themselves up as they like.

Its not 100% clear to me what you're asking, but does this help?

System | Preferences | Windows | "Select Windows when mouse moves over them"

---

### Post by kruschev on 2006-11-17
no localuser, that's not it. apps often send some signal to say they want to appear above all other apps - not when the mouse goes over. in kde, they pop up (this setting can be modified). in gnome, the icon in the task bar just flashes.

it's not just matlab, there are other cases where i don't like this behaviour.

---

### Post by localuser on 2006-11-17
> **kruschev said:**
> eno localuser, that's not it. apps often send some signal to say they want to appear above all other apps - not when the mouse goes over.

Yes, I did some research after posting my reply...that will teach me to keep my mouth shut until I know what's being asked :-#

From what I read elsewhere on the Net, it seems that its not possible to make that change in Gnome, as you've probably already surmised.

---

### Post by localuser on 2006-11-17
> **kruschev said:**
> eno localuser, that's not it. apps often send some signal to say they want to appear above all other apps - not when the mouse goes over.

Yes, I did some research after posting my reply...that will teach me to keep my mouth shut until I know what's being asked :-# :mrgreen:

From what I read elsewhere on the Net, it seems that its not possible to make that change in Gnome, as you've probably already surmised.

---

### Post by Nekiruhs on 2007-07-31
Sorry to necro-post but this is annoying me as well. All my new windows show up unfocused, its so annoying to have an app open in the background and launch it several times before realizing its in the background. Any fix for this?

---

### Post by mcduck on 2007-08-01
Are you using Compiz (or the Desktop Effects) or Beryl? Because I've never seen that happen with the default window manager, Metacity..

---

### Post by sedd on 2007-08-10
> **mcduck said:**
> Are you using Compiz (or the Desktop Effects) or Beryl? Because I've never seen that happen with the default window manager, Metacity..

Try this, mcduck. Open firefox from the main menu, and open some page. Then open a terminal and type 'firefox'. Focus will be left on the terminal, even though you've made it quite clear that you'd like to use firefox now. It doesn't seem to happen when the 2nd app is launched from any gnome component, such as the main menu or alt-f2.

---

