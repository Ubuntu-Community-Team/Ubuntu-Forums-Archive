---
title: "Uploading and saving files in Firefox with Konqueror."
date: 2006-01-19
forum: General Help
---

### Post by McSnuffy on 2006-01-19
My problem started when I installed Firefox 1.5.
You see, before I re-installed Firefox, whenever I wanted to save or upload an image, I would be able to do so through Konqueror. For example, if I were to click "browse" on imageshack.us, a Konqueror window would pop up to allow me to select the file that I wanted to upload. (see thumbnail below)

[[IMG]http://img4.imageshack.us/img4/6886/uploadk7qs.th.png[/IMG]](http://img4.imageshack.us/my.php?image=uploadk7qs.png)

However, after re-installing Firefox, I have to upload through GNOME's file browser for some reason. (see thumbnail below) It is harder to navigate and I have no idea how to do certain things in it, so I'd perfer to upload through Konqueror. Is there some sort of way to set Firefox  to upload files through Konqueror again? Or do I have to do something else?

[[IMG]http://img4.imageshack.us/img4/9499/uploadg0ig.th.png[/IMG]](http://img4.imageshack.us/my.php?image=uploadg0ig.png)

Sorry if the wording on this isn't very clear. I'm not sure if I'm calling everything by it's correct name. (That's why I included images.) Thanks in advance for your help and time.

---

### Post by NeoChaosX on 2006-01-19
Actually, that applet is called KDialog. I believe it was used in Firefox for awhile, but lately, Firefox now seems to be defaulting to GTK/Gnome dialogs, as Mozilla has made GTK integration a priority in Firefox. There's been a couple hacks to use either KDialog or the file picker that's built into Firefox with Linux. This [guide](http://www.ubuntuforums.org/showthread.php?t=110353&highlight=firefox) I wrote offers a way to get the built-in dialogs. I know of one hack to use KDialog in Firefox (it's on Mozillux.com), but it freezes Firefox while the dialog is open and is really buggy. So yeah, you're stuck between a rock and a hard place right now. :???:

---

### Post by McSnuffy on 2006-01-19
Thanks a lot for the help and the clarification. Your guide looks pretty straightfoward. Hopefully, it will be useful.

**Edit:**

Hum. I seem to be having a problem. I edited the file as I should have, but Firefox still refers to the GTK Dialogue. Here is the code that appers in my file:
 
>     compMgr.registerFactoryLocation(FILEPICKER_CID,
                                    "FilePicker JS Component",
//@line 278 "/builds/tinderbox/Fx-Mozilla1.8/Linux_2.4.21-27.0.4.ELsmp_Depend/mozilla/xpfe/components/filepicker/src/nsFilePicker.js.in"
                                    FILEPICKER_CONTRACTID,
//@line 280 "/builds/tinderbox/Fx-Mozilla1.8/Linux_2.4.21-27.0.4.ELsmp_Depend/mozilla/xpfe/components/filepicker/src/nsFilePicker.js.in"
                                    fileSpec,
                                    location,
                                    type);

I save, exit, and go into Firefox. However, I still upload through GTK.

---

### Post by NeoChaosX on 2006-01-19
Oh. Try installing or disabling an extension, then restart Firefox.

---

### Post by McSnuffy on 2006-01-19
I was able to disable an extension (ForecastFox) just fine. When I restarted Firefox, it was disabled.

---

### Post by NeoChaosX on 2006-01-20
So do the dialogs work? What disabling the extension should do is get Firefox to recognize the changes made in the file.

---

### Post by McSnuffy on 2006-01-20
Very odd. All last night, the changes were not being recognized, but I just tried it this morning and KDialogue came up. 8) 

Thank you very much for your help.

---

### Post by stimpack on 2006-01-20
Wow at last a proper file dialog! Many thanks NeoChaosX, Im glad to be rid of the ghastly GTK junk.

---

