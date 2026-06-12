---
title: "Shift+Delete is insane!"
date: 2006-06-21
forum: Desktop Environments
---

### Post by vyruss on 2006-06-21
**Shift+Delete**: This shortcut is the universal IBM standard for **Cut** ever since I started using a PC exactly 20 years ago and it works on *every* platform I've ever used, except Ubuntu/Gnome, where **it means Delete File in Nautilus**!

It is simply insane to assume that pressing Shift+Delete should do the same thing as pressing Delete by itself!

What's worse, there's *no way to change this* from within the Gnome interface. Is there an *easy* way to do this?
(When replying *please* take in mind that I could find a way to do it by tweaking X configs, but *the average user cannot*.)


(I'm seriously considering submitting this as a bug to Gnome, but knowing some developers' attitude there, I doubt that will get me anywhere.)

[B]*EDIT*: Let me clarify:
This behaviour is unacceptable when *renaming* files in Nautilus[/B]

---

### Post by glotz on 2006-06-21
So you never used Microsoft Windoze? And pressing shift+delete is not the same as pressing delete. (adding shift will actually delete the file instead of placing it to you trash, just like on W)

I have no idea if you can change that.

---

### Post by Demon012 on 2006-06-21
Try Shift + Insert on your keyboard that will paste for you in Ubuntu and is pretty universal for Linux and also works within Windows.

---

### Post by vyruss on 2006-06-21
[QUOTE=glotz]So you never used Microsoft Windoze? And pressing shift+delete is not the same as pressing delete. (adding shift will actually delete the file instead of placing it to you trash, just like on W)

I have no idea if you can change that.[/QUOTE]

Let me give you an example: When renaming a file in Windows, **Shift+Delete** inside the filename box will **Cut** the selected part of the filename. In Ubuntu, it will try to **Delete** the file!

I didn't mean that Shift+Delete is exactly the same as Delete literally, but they do roughly the same action, instead of what has come to be expected by most users.

---

### Post by lamego on 2006-06-21
Shitft-Delete is the "standard" delete without going to the recycle bin key combination on Windows as far I can remember.
No matter how many people hate it, Windows is still the most used desktop plataform so I believe is kind of logical keeping it the same way on Nautilus.
About the ability to change an worldwide established key combination behavior on nautilus I would classify it as a feature request, not a bug.

---

### Post by vyruss on 2006-06-21
[QUOTE=Demon012]Try Shift + Insert on your keyboard that will paste for you in Ubuntu and is pretty universal for Linux and also works within Windows.[/QUOTE]

I had a typo, now it's corrected. I meant to say ***Cut***.

---

### Post by Jucato on 2006-06-21
Delete doesn't really delete a file. It only moves the file to the Trash bin/directory, where it can be recovered or permanently deleted.
Shift+Delete permanently deletes a file. no more recoveries.

I always thought that since the advent of Windows 3.1 (or was it 95?) that the universal shortcut for cut was Ctrl+X?

---

### Post by Harleen on 2006-06-21
This handling of Shift+Delete is consistent with Windows and KDE.
When handling files, it deletes them without using the trash folder. When handling text, it cuts the text in the buffer. Why should GNOME make an exception here if it works like that the other systems?
I agree that this key combination was no good choice, but neither was using CTRL+C as shortcut for copying instead of aborting. And that irritated me even more back than...

---

### Post by vyruss on 2006-06-21
[QUOTE=Fenyx]Delete doesn't really delete a file. It only moves the file to the Trash bin/directory, where it can be recovered or permanently deleted.
Shift+Delete permanently deletes a file. no more recoveries.

I always thought that since the advent of Windows 3.1 (or was it 95?) that the universal shortcut for cut was Ctrl+X?[/QUOTE]

Nope, Microsoft included it to make it easy on the Mac users :)

***Let me clarify:***
This behaviour is **unacceptable** when **renaming** a file in Nautilus.

---

### Post by vyruss on 2006-06-21
[QUOTE=Harleen]When handling text, it cuts the text in the buffer[/QUOTE]

Not always. Try renaming a file in Nautilus (F2) and pressing (Shift+Delete).

---

### Post by Harleen on 2006-06-21
I'm not using GNOME. But if it behaves as you say, I also would call this a bug.

---

### Post by bluenova on 2006-06-21
[QUOTE=vyruss](I'm seriously considering submitting this as a bug to Gnome, but knowing some developers' attitude there, I doubt that will get me anywhere.)[/QUOTE]
Please don't submit it as a bug, my whole computing life (10 years 4 O/S's) Shift+DEL has always removed the file rather than moving to the rubbish bin. I would be very annoyed if it no longer worked.

---

### Post by glotz on 2006-06-21
I think that it is a little surprising. What do other OSes do in similar situation? Can't remember.

---

### Post by vyruss on 2006-06-21
[QUOTE=bluenova]Please don't submit it as a bug, my whole computing life (10 years 4 O/S's) Shift+DEL has always removed the file rather than moving to the rubbish bin. I would be very annoyed if it no longer worked.[/QUOTE]

How many more times do I have to clarify this?

It shouldn't do this when you're renaming the file. It's a text box with selected text you're trying to cut, not delete the file instead.

---

### Post by bluenova on 2006-06-21
[QUOTE=vyruss]How many more times do I have to clarify this?

It shouldn't do this when you're renaming the file. It's a text box with selected text you're trying to cut, not delete the file instead.[/QUOTE]
In this situation I would use CNTL+X, DEL just doesn't make sence (to me).

---

### Post by vyruss on 2006-06-21
[QUOTE=bluenova]In this situation I would use CNTL+X, DEL just doesn't make sence (to me).[/QUOTE]

I'm talking about Shift+Del, and yes it does make sense to a lot of people unfortunately :/ Especially since in every other text entry box in Gnome it Cuts Text.

---

### Post by Jucato on 2006-06-21
I can say that this does not happen in KDE, though. I've tested it. Press a file (F2) and press Shift+Del doesn't do anything. It clears the text box but does not Cut the text. I think it's related to the fact that Shift+Del is mapped to Delete (permanent) and not to Cut. 

I agree w/ you vyruss, this should not happen. Shift+Del, whether it is mapped to Delete or to Cut, should not delete the file **while you are renaming a file**

Just a bit of info for those who might not have understood a bit. The real issue is this: When you try to rename a file, an editable text box appears, highlighting the name of the file. Supposedly, it is the filename that receives the focus, not the file itself. Logically, when you press something, like Del or any other key, it should only affect the text of the filename, right? So when you press Shift+Del, even if it is mapped to to Delete (permanently), it should not delete the file itself, but only the text of the filename. Whether Shift+Del is mapped to Delete or to Cut is irrelevant in this situation.

Am I getting you right, vyruss?
While I don't have a handy solution (not even for KDE), might I suggest that you start to use the Ctrl+C,X,V shortcuts, as it seems that they are becoming more standard that the previous Ctrl+Ins (which I still use in the terminal because Ctrl+C is reserved for Cancel), Shift+Del, and Shift+Ins. Those keys (the X,C,V) are also easier to reach with one hand anyway. It's just a suggestion. Please don't take offense.

---

### Post by vyruss on 2006-06-21
[QUOTE=Fenyx]Just a bit of info for those who might not have understood a bit. The real issue is this: When you try to rename a file, an editable text box appears, highlighting the name of the file. Supposedly, it is the filename that receives the focus, not the file itself. Logically, when you press something, like Del or any other key, it should only affect the text of the filename, right? So when you press Shift+Del, even if it is mapped to to Delete (permanently), it should not delete the file itself, but only the text of the filename. Whether Shift+Del is mapped to Delete or to Cut is irrelevant in this situation. Am I getting you right, vyruss? [/quote]

Absolutely right.

> While I don't have a handy solution (not even for KDE), might I suggest that you start to use the Ctrl+C,X,V shortcuts, as it seems that they are becoming more standard that the previous Ctrl+Ins (which I still use in the terminal because Ctrl+C is reserved for Cancel), Shift+Del, and Shift+Ins. Those keys (the X,C,V) are also easier to reach with one hand anyway. It's just a suggestion. Please don't take offense.

Not at all. However I find that I've always used Shift+End, Shift+Home, Shift+Insert and Shift+Delete for this sort of thing, especially when I have both hands on the keyboard.

Now **the real problem** is not what shortcuts someone is used to, but the **inconsistency** in the GUI. Every other **text input box** I could find in Gnome and Firefox accepted Shift+Delete as **Cut** so it is only logical to assume that the **renaming** text box does as well.

---

### Post by neutro on 2006-06-21
> Now the real problem is not what shortcuts someone is used to, but the inconsistency in the GUI. Every other text input box I could find in Gnome and Firefox accepted Shift+Delete as Cut so it is only logical to assume that the renaming text box does as well.

As far as I can see, Vyruss is completely right about this, and a bug report is in order, in my opinion. As stated previously, when part of the filename is highlighted in a Nautilus icon, you wouldn't think hitting a key combo would affect the file itself. Moreover, in other circumstances (for example, editing text in a Nautilus URL box), selecting text and hitting shift+delete actually cuts the text as he describes.

Maybe the problem is that fewer and fewer developers remember those legacy shortcuts :mrgreen:

---

### Post by vyruss on 2006-06-21
[QUOTE=neutro]As far as I can see, Vyruss is completely right about this, and a bug report is in order, in my opinion. As stated previously, when part of the filename is highlighted in a Nautilus icon, you wouldn't think hitting a key combo would affect the file itself. Moreover, in other circumstances (for example, editing text in a Nautilus URL box), selecting text and hitting shift+delete actually cuts the text as he describes.

Maybe the problem is that fewer and fewer developers remember those legacy shortcuts :mrgreen:[/QUOTE]

I filed the bug and some developer spotted it as a duplicate. It appears that what is causing this, is that the text box appearing over the filename does not have focus for the keyboard shortcuts, but rather the underlying Nautilus window does. So instead of correctly cutting from the text box, it tries to delete from the Nautilus window. They say it will be fixed in time for Gnome 2.15. I sure hope so!

Original bug: [http://bugzilla.gnome.org/show_bug.cgi?id=314431](http://bugzilla.gnome.org/show_bug.cgi?id=314431)

---

### Post by Jucato on 2006-06-21
[QUOTE=vyruss]It appears that what is causing this, is that the text box appearing over the filename does not have focus for the keyboard shortcuts, but rather the underlying Nautilus window does. So instead of correctly cutting from the text box, it tries to delete from the Nautilus window.[/QUOTE]

Just as I suspected. One thing that puzzles me. How come Ctrl+X doesn't cut the file, too? (I'm presuming it doesn't). Does this bug only happen with Shift+Del or with other keyboard shortcuts as well?

Also, couldn't they make an intermediate release for bug fixes? Something like GNOME 2.14.x?? Or do you really have to wait for 6 months (that's the GNOME development cycle, right?) for it to be fixed?

---

### Post by vyruss on 2006-06-21
[QUOTE=Fenyx]Just as I suspected. One thing that puzzles me. How come Ctrl+X doesn't cut the file, too? (I'm presuming it doesn't). Does this bug only happen with Shift+Del or with other keyboard shortcuts as well? Also, couldn't they make an intermediate release for bug fixes? Something like GNOME 2.14.x?? Or do you really have to wait for 6 months (that's the GNOME development cycle, right?) for it to be fixed?[/QUOTE]I'm not directly involved in Gnome development so I can't really tell. But, from the bug report:

"The issue is that the key-press-event handler of GtkWindow picks up the GtkActions keybindings before the widgets' handlers, using gtk_window_activate_key. I came up with the patch on the mailing list but our widgets eat too many key bindings, which is not good. Let's fix this up during the 2.15 cycle (i.e. now)."

---

### Post by Jucato on 2006-06-21
Yes, I've read the bug report. It seems that Shift+Del is not the only thing affected. What bothers me is that they will be waiting for the next minor release to fix this properly, as it is, IMHO, a very serious issue, especially with Shift+Del (although the percentage of people using that shortcut nowadays might be low).

But I'm no developer, so maybe I have shouldn't complain. :D

---

