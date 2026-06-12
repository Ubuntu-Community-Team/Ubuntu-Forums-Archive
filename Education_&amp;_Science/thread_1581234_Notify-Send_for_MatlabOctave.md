---
title: "Notify-Send for Matlab/Octave"
date: 2010-09-24
forum: Education &amp; Science
---

### Post by LukeMasters on 2010-09-24
Hi everybody!

I recently wrote a little Matlab function to send notifications to libNotify.

[http://www.mathworks.com/matlabcentral/fileexchange/28809-notify-send](http://www.mathworks.com/matlabcentral/fileexchange/28809-notify-send)

[IMG]http://www.mathworks.com/matlabcentral/fx_files/28809/1/screenshot.png[/IMG]

I tried it with octave without any problems. This is ideal for those long running jobs. This way you don't have to check matlab/octave all the time to see when it's done.

---

### Post by darkstarbyte on 2010-09-25
I envy you. You are a programmer with a promising future.

---

### Post by gunksta on 2010-09-28
Very interesting. I have been wanting to sit down and learn launchpad/bzr and I think I am going to copy your idea and do the same thing for R.

Someone may have already do it, but perhaps I'll be able to do it better.

---

### Post by carandraug on 2010-09-30
> **LukeMasters said:**
> Hi everybody!

I recently wrote a little Matlab function to send notifications to libNotify.

[http://www.mathworks.com/matlabcentral/fileexchange/28809-notify-send](http://www.mathworks.com/matlabcentral/fileexchange/28809-notify-send)

[IMG]http://www.mathworks.com/matlabcentral/fx_files/28809/1/screenshot.png[/IMG]

I tried it with octave without any problems. This is ideal for those long running jobs. This way you don't have to check matlab/octave all the time to see when it's done.

There's an [octave-zenity package]("http://octave.sourceforge.net/zenity/index.html") which among other things, supports notifications.

```

zenity_notification (text, icon)

```

It's part of the Ubuntu repositories.

If you download the development version with SVN, it's much more complete. Other than a one-time notifications, the function you can create a icon on the toolbar and use standard error, info, question and warning icons. The whola package allows to create many dialog boxes such as file selection, error messages, list of options with radio buttons or check boxes.

---

