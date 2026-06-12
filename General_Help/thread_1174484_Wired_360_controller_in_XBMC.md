---
title: "Wired 360 controller in XBMC"
date: 2009-05-31
forum: General Help
---

### Post by femngi on 2009-05-31
Running Ubuntu 9.04 - Jaunty Jackalope I use an Xbox 360 controller usually without any issue on the default drivers. However I was surprised to discover that it didn't work with XBMC at all. Some searching lead me to /usr/share/xbmc/system/keymap.xml which I flumblingly tried to edit with no visible effect. All the guides on this subject are for the wireless controller and I would be grateful if someone could clear up what is probably a very simple matter.

---

### Post by femngi on 2009-05-31
Since xpadder isn't on linux I tried using joy2key however when I try to run it joy2key tells me:
```
Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

```
And sure enough jscalibrator confirms that my device is under /dev/input/js0
Joy2key doesn't seem to know what to do about this, are there any alternatives to this application available?

---

### Post by blueorder on 2009-05-31
> **femngi said:**
> Since xpadder isn't on linux I tried using joy2key however when I try to run it joy2key tells me:
```
Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

```
And sure enough jscalibrator confirms that my device is under /dev/input/js0
Joy2key doesn't seem to know what to do about this, are there any alternatives to this application available?

Maybe this post will help?

[Link]("http://ubuntuforums.org/showpost.php?p=174600&postcount=4")

**EDIT**

or this one?

[Link 2]("http://ubuntuforums.org/showthread.php?t=312569")

---

### Post by femngi on 2009-05-31
Thanks for the help but I've only managed to progress to another error message. Joy2key now says:
```
Must specify a target!

```And ```
# joy2key -dev /dev/input/js0
#joy2key -dev /dev/js0
```etc all give the same result. 
I should probably have tagged this thread as joy2key.
Sorry for all the hand holding, I've been using linux for as long as I've been on this forum.
[B]EDIT
[/B]I am now adjusting the keymap.xml since by changing <joystick name="Microsoft Xbox Controller S"> to <joystick name="Microsoft Xbox 360 pad">
I can get some kind of response from some of the buttons although they're mapped strangely. Changing the button ids hasn't done anything so far but I haven't yet updated the whole file.
[B]EDIT2
[/B]No luck. Despite editing the entire file the keys still don't map properly. I was using jscalibrator to get the button id and using the format ```
 <joystick name="Microsoft X-box 360 pad">
      <altname>Mad Catz MicroCON</altname>
      <altname>Logitech Xbox Cordless Controller</altname>
      <button id="6">Close</button>
      <button id="1">PreviousMenu</button>
      <button id="10">PreviousMenu</button>
    </joystick>
```All that happens is the rbumper button selects and the A button goes back and only on the file browser screen.
It probably isn't xbmc needing to reload keymap.xml as it broke instantly when I changed the <gamepad> input.

---

### Post by femngi on 2009-05-31
I have since replaced the MadCatz altname instead of the controller S one which results in more controls working in a more predictable fashion. However the changes in button ids is still not affecting the program so I can use the buttons but not the dpad to select. I'm still surprised there is a playstation controller configuration in the default setups but no 360 one. How long has it been since this file was updated?

---

### Post by femngi on 2009-06-01
Solved by replacing xpad with xboxdrv as explained here: [http://www.stolennotebook.com/anthony/2008/09/13/using-xbmc-for-linux-with-an-xbox-360-wireless-controller-and-the-userspace-usb-driver-xboxdrv/](http://www.stolennotebook.com/anthony/2008/09/13/using-xbmc-for-linux-with-an-xbox-360-wireless-controller-and-the-userspace-usb-driver-xboxdrv/)

---

