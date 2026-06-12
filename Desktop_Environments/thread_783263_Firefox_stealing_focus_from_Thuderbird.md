---
title: "Firefox stealing focus from Thuderbird"
date: 2008-05-05
forum: Desktop Environments
---

### Post by Ghostlove on 2008-05-05
When I am reading an email in Thuderbird and I click a link, the link opens in Firefox as it should, but in doing so Firefox steals the focus. This is really annoying when I have several links I want to open. It didn't happen before I upgraded Firefox - is there a way to stop it happening now?

---

### Post by Bubba64 on 2008-05-05
> **Ghostlove said:**
> When I am reading an email in Thuderbird and I click a link, the link opens in Firefox as it should, but in doing so Firefox steals the focus. This is really annoying when I have several links I want to open. It didn't happen before I upgraded Firefox - is there a way to stop it happening now?

I am not dure by what Steal the focus means. What are you losing from Thunderbird.

---

### Post by Ghostlove on 2008-05-05
It means that Firefox puts itself 'on top' of Thunderbird instead of staying underneath it.

---

### Post by Bubba64 on 2008-05-05
> **Ghostlove said:**
> It means that Firefox puts itself 'on top' of Thunderbird instead of staying underneath it.

If you go into FF edit-preferences-tabs you can change whether it opens on a new page or a tab I think if you mark tab it will be the way you want. I think though that is where you can change it. I tried this change myself and it seemed to not make a difference, on my desktop, but my laptop automatically opens the link under thunderbird.

---

### Post by Ghostlove on 2008-05-05
It is already marked to open a new tab - and it does open a new tab. It just takes the focus away from Thunderbird as it does so.

---

### Post by Ghostlove on 2008-05-06
I still haven't managed to fix this; any ideas, anyone?

---

### Post by Bubba64 on 2008-05-06
[QUOTE=Ghostlove;4893616]I still haven't managed to fix this; any ideas, anyone?[/QUOTE

I couldn't find an answer to your problem, but there is a applications in synaptic called all tray which you can use to put other applications in the notification tray, I use it for Thunderbird so that if I get an email I know immediately, but the other use is that as soon as I click on the Thunderbird Icon in the tray it is on or off the screen. Good Luck

---

### Post by ft77 on 2008-05-16
Type about:config into the address bar in Firefox.
In the Filter box type "diverted"
It will find the result "browser.tabs.loadDivertedInBackground"
By default the option is set to false. Double click it to set it to true. Now the links will be opened without stealing Thunderbird's focus.

---

### Post by O_Breda on 2009-02-11
If you're interested in my solution for this:
[http://getaresultnow.com/how-to-click-on-a-link-in-thunderbird-link-that-opens-in-firefox-without-losing-focus-on-thunderbird/](http://getaresultnow.com/how-to-click-on-a-link-in-thunderbird-link-that-opens-in-firefox-without-losing-focus-on-thunderbird/)

Hope it helps you. :)

---

