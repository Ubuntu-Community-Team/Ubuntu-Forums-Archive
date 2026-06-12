---
title: "Kunbuntu: How to make Firefox the default browser???"
date: 2006-08-31
forum: Desktop Environments
---

### Post by martin_d on 2006-08-31
How do I make Firefox the default browser in Kubuntu???

Whenever I click on a link in Thunderbird, Konqueror opens.

---

### Post by paddy1978 on 2006-08-31
Hi,

If you go to Edit>Preferences, then select Advanced, on the 'General' tab is a button to open the 'config editor'. (It's like the screen you get when you go to "about:config"  in Firefox.)

There's a key called 'network.protocol-handler.app.http' (and one for https). Default is 'x-www-browser'. If you change this to 'firefox' it seems to work!

---

### Post by xyz on 2006-08-31
Hi-

I work with Ubuntu but Firefox being Firefox, I assume it's the same?
Click on 'Edit' and then 'Preferences' and finally on the 'General' tab.

Under 'Default Browser' you'll read: "Firefox should check if it is the default browser when starting"...activate it and then click on "Check now".

Should work.

---

### Post by martin_d on 2006-08-31
Thanks a lot, it works!

---

### Post by Noiano on 2006-09-05
it doesn't work to me....konqueror still opens...check now button seems not to respond. Besides i have choosen firefox also in kde components->default web broswer...

I hope we can fix this...

Thanks

---

### Post by paddy1978 on 2006-09-05
In my experience, it seems that Thunderbird does not look at the setting in kde components->default web broswer.

In my post above (where I mention going to Edit>Preferences, etc... and changing the network-protocol key) I am talking about doing this in Thunderbird, not Firefox. I see that I didn't make this explicit, so could you confirm that you've done this correctly?

---

### Post by Noiano on 2006-09-06
> **paddy1978 said:**
> In my experience, it seems that Thunderbird does not look at the setting in kde components->default web broswer.

In my post above (where I mention going to Edit>Preferences, etc... and changing the network-protocol key) I am talking about doing this in Thunderbird, not Firefox. I see that I didn't make this explicit, so could you confirm that you've done this correctly?

Confirmed...I changed the default setting to "firefox" and now works...but I cannot understand why thunderbird doesn't use the default broswer...I've choosen firefox so sould't be necessary to change the setting also in thunderbird....

Thanks again

---

### Post by martin_d on 2006-09-06
You need to change it with "update-alternatives"

---

### Post by Noiano on 2006-09-07
> **martin_d said:**
> You need to change it with "update-alternatives"

sorry i didn't got that!....i only can say that conqueror always starts, with kopete and each hyperlink. Besides with evolution simply no broswer starts....how do I fix it?

---

### Post by Noiano on 2006-09-12
up.....please help me!

---

### Post by martin_d on 2006-09-12
1. Open a shell
2. Run "sudo update-alternatives --list x-www-browser". You should see a list of availible browsers.
3. Run "sudo update-alternatives --set x-www-browser /usr/bin/firefox" to select Firefox as the default browser.

---

### Post by Noiano on 2006-09-13
> **martin_d said:**
> 1. Open a shell
2. Run "sudo update-alternatives --list x-www-browser". You should see a list of availible browsers.
3. Run "sudo update-alternatives --set x-www-browser /usr/bin/firefox" to select Firefox as the default browser.
thanks....it works...many many thanks

---

### Post by whiterabbit on 2006-10-06
> **martin_d said:**
> 1. Open a shell
2. Run "sudo update-alternatives --list x-www-browser". You should see a list of availible browsers.
3. Run "sudo update-alternatives --set x-www-browser /usr/bin/firefox" to select Firefox as the default browser.I was having the same problem, thanks martin.  Just goes to show how powerful the command line is, even if used for simple things like this. :D

---

### Post by rev on 2006-10-07
Thank you, martin_d!
Sometimes check-box-click-ok solutions just don't work...

---

### Post by Theely on 2006-10-17
There is another way to do this as well, since doing the update-alter... doesn't fix it all the time.

Open Konqueror.
Settings -> Configure Konqueror -> File Associations
Click on the [+] Next to "text"
Highlight "html"

Over on the right side you'll see Application Order, make FireFox the top listing. That will make FF open all html file before anything else will.

Now you can change anything to open with whatever App you want!

Cheers.

---

### Post by kwood129 on 2006-11-07
I found that changing the options in System settings under default applications seems to work fine.  Go to the Web Browswer option then change the default component to firefox.  It will allow you to browse your programs to add firefox as the default.  After that click on apply and it works perfect.

---

### Post by henriquemaia on 2008-06-30
> **martin_d said:**
> 1. Open a shell
2. Run "sudo update-alternatives --list x-www-browser". You should see a list of availible browsers.
3. Run "sudo update-alternatives --set x-www-browser /usr/bin/firefox" to select Firefox as the default browser.

Thanks for this post and for your help. I was wondering about how to do this and found your advice. I have tried it and it has worked.

---

