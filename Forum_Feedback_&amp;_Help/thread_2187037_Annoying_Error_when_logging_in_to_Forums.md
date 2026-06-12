---
title: "Annoying Error when logging in to Forums"
date: 2013-11-10
forum: Forum Feedback &amp; Help
---

### Post by Petro Dawg on 2013-11-10
Just curious if anyone else is having this issue...  I've noticed lately, every time I log into the forums using Google Chrome I am met with the following error...

[IMG]http://farm4.staticflickr.com/3730/10781447313_432ff1a545_o.png[/IMG]
This happens every time after the "Personal Data Request" page during login when I click the "Yes, log me in" button.

Once I click the "back" button from the error message screen I am directed back to the Ubuntu Forums main page and can continue navigating the site as usual from there.  I can recreate the issue consistently with Chrome, but it does not appear when using Firefox.  

I'm not aware of making any changes to any settings in Chrome lately and I didn't used to have this issue, so I'm not sure what might be causing the problem.

---

### Post by coffeecat on 2013-11-10
You posted in the Resolution Centre where only the OP and forum staff are able to post to threads, so you wouldn't get much feedback if others are experiencing this issue! I'll move this to FF&H. I haven't seen this with either Firefox or Chromium, so it will be useful to know if others are seeing this with Chrome.

*Thread moved to **Forum Feedback & Help**.*

---

### Post by Petro Dawg on 2013-11-10
No problem.  I wasn't sure where to post this one.  Thanks for the help.

---

### Post by Petro Dawg on 2013-11-13
Bump.

I've tried [re-downloading]("https://www.google.com/intl/en/chrome/browser/"), re-installing the Google Chrome Browser, and re-booting my system.  I still have the error message shown on my first post when ever I first log in to these forums using Chrome.  Anyone else experiencing this issue?  If not, any ideas what might be going on and how I might fix it?

---

### Post by PaulW2U on 2013-11-16
> **Petro Dawg said:**
> I've tried [re-downloading]("https://www.google.com/intl/en/chrome/browser/"), re-installing the Google Chrome Browser, and re-booting my system.  I still have the error message shown on my first post when ever I first log in to these forums using Chrome.  Anyone else experiencing this issue?  If not, any ideas what might be going on and how I might fix it?

I also use Chrome, amongst other browsers, and don't have this problem. Re-installing an application often doesn't help as removing an application doesn't remove the application's settings which are saved in your home directory. Have you tried clearing your browsing data from within Chrome?

Then there's always the options of creating a new user on your PC and logging on with the new account or removing/renaming existing settings so that Chrome creates a new profile and default settings when it's restarted. I would try to clear browsing data first though.

---

### Post by Petro Dawg on 2013-11-16
> **PaulW2U said:**
> I also use Chrome, amongst other browsers, and don't have this problem. Re-installing an application often doesn't help as removing an application doesn't remove the application's settings which are saved in your home directory. Have you tried clearing your browsing data from within Chrome?

Then there's always the options of creating a new user on your PC and logging on with the new account or removing/renaming existing settings so that Chrome creates a new profile and default settings when it's restarted. I would try to clear browsing data first though.

Thanks for the advice, it was most helpful.  I even tried deleting the "google-chrome" folder in the /Home/.config directory and re-installing which still didn't work.  Which makes me wonder where on earth (or my PC) is google chrome actually saving user settings?  And I'm still not sure what I did to create the problem in the first place.

However, I finally figured out all that really needs to be done is to click the "Delete this User" in the settings window.  It seems a new user doesn't have to be created since it will just replace the default user with a new default. 

[ATTACH=CONFIG]247871[/ATTACH]

Other than losing my bookmarks (not a big deal), everything appears to be working perfectly again.

Update:
Once I signed into Google and synced my browser, my old bookmarks re-appeared.

---

