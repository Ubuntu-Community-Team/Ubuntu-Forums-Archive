---
title: "problems with firefox and chromium"
date: 2014-05-23
forum: Desktop Environments
---

### Post by srope01 on 2014-05-23
Been having problems with Lubuntu 14.04 installation. The URL bar in Firefox is blanked out (see screenshot attached). I can work with it by selecting the blanked out section and then hit carriage return to get rid of of whatever text is there and then the blanked out part gets cleared and I can see what I would type. I reinstalled Firefox, but no change. Anyone else got this problem and can anyone help?

In order to get around this problem temporarily, I installed Chromium via synaptic. This presented another problem. Typing into any field does not work (URL bar, search form, any web form). The mouse works so that the cursor appears in the form but I just can't enter anything using the keyboard.

So I have two broken browsers installed. Any ideas on either of these problems?

---

### Post by Dennis N on 2014-05-23
**Fix for the Chromium text entry problem in Lubuntu 14.04:**

Preferences > Language Support > (close any pop up window that appears) > Keyboard Input Method System > change from ibus to none.

**Firefox Address Bar:**

Known Bug - Another thread about it:

[http://ubuntuforums.org/showthread.php?t=2221850](http://ubuntuforums.org/showthread.php?t=2221850)

Maybe some workarounds or suggestions in there.

---

### Post by srope01 on 2014-05-23
```
[COLOR=#000000]
Preferences > Language Support > (close any pop up window that appears) > Keyboard Input Method System > change from ibus to none.[/COLOR]
```

Thanks, that solves the chromium problem.

```

[COLOR=#000000]Known Bug - Another thread about it:[/COLOR]

[http://ubuntuforums.org/showthread.php?t=2221850](http://ubuntuforums.org/showthread.php?t=2221850)
```

The thread is suggesting to wait until the developers fix this. That might take a while. No workarounds suggested so I decided to switch to chromium.

---

### Post by vasa1 on 2014-05-23
> **srope01 said:**
> ... No workarounds suggested so I decided to switch to chromium.
If you mean the unreadable address bar in Firefox, did you try:
```
go to about:config, set gfx.xrender.enabled to false, restart the browser, and retry
```from [https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c23](https://bugzilla.mozilla.org/show_bug.cgi?id=1005501#c23) . 
Or did you try and it didn't work for you?

---

### Post by srope01 on 2014-05-24
```
go to about:config, set gfx.xrender.enabled to false, restart the browser
```

Yes, that worked, thanks. So a workaround each for firefox and chromium means this thread can be set to solved.

---

