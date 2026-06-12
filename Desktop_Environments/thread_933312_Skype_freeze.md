---
title: "Skype freeze"
date: 2008-09-29
forum: Desktop Environments
---

### Post by max7 on 2008-09-29
I have to use skype but it does not work well on ubuntu.

When I click on options -> Sound device. It freeze.
Contact list is not loading online contacts.
Other people do not see me online.
I thought skype does not work well on linux but I recently I saw Ubuntu Remix video and skype was shown to work. 

Does skype work well on your PC?

Does someone know what must be done for skype to start working?

I have a USB phone that is recognized by linux as usb audio.
Standard audio is also working.

Thanks

---

### Post by roadkill101 on 2008-10-06
When does skype freeze up? I was having a similar problem, where skype would freeze when I clicked on the sound devices option. This only happened after I had made a few calls, and then calling stopped working and the freezes occured.

I was able to avoid this problem simply by choosing a different option in the sound devices menu right when skype opened, before it had a chance to freeze. Now it works perfectly.

At [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html) they provide some advice on sound issues. If you are unable to initially change sound devices, I would follow the advice at this site.

---

### Post by windfix on 2008-11-09
I am having similar problems:  Skype 2.0 freezes as soon as I click on Sound Devices.  I had it working fine for a week or so after installing Intrepid, though it had done this too me under Hardy as well.

A few days ago, I had it working fine on Bluetooth for Ringing and Sound Out, never did work for the Sound In - but point being I could switch between Sound devices just fine.  Now, it just freezes. I thought I'd put it back on default settings, I don't think it was set to Bluetooth when it started freezing again.  Chat still works, calls do not.

(edit: it actually unfreezes after a 2.5 minute grey-out; and sound tests come through after a 50 second delay - really wierd)

I use Skype nonstop at work to keep in touch with my staff - and now I'm stuck back in XP or OSX just for Skype.  Driving me nuts.

---

### Post by windfix on 2008-11-09
OK, I found a workaround that might help someone else:

First, I changed all my system sound settings to "HDA Intel ALC885 Analog (OSS)", where they had all been set to ALSA before.  I tested sound via Amarok, etc. and it still worked.

Then, I uninstalled Skype and installed the OSS variant version via Synaptic.  Now the only sound options in Skype are /dev/dsp, but it works.

---

