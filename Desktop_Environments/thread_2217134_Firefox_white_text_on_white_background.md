---
title: "Firefox: white text on white background"
date: 2014-04-15
forum: Desktop Environments
---

### Post by sowdust on 2014-04-15
Hi everyone,  I'm running Xubuntu 13.04 with a dark theme and have Firefox 29 running. It might be worth mentioning that I had experienced the same problem with the stable firefox version around a year ago (reason why I used chromium for a while).  The problem is that on some pages (eg. youtube) the input fields have a white background and the text color is white too - making what I type unreadable.  In the preferences I have set the colors as follow: Black text White background Do NOT use system colors Allow websites to use their own colors   I have tried adding some style directives to the ~/mozilla/firefox/default/chrome/userChrome.css file but this seems to overwrite only firefox appearance (eg. the url bar) and not the actual web page styles.  Looking up the problem I have also tried some other suggested solutions, such as deactivating the hardware acceleretion, but with no results.  Any ideas on how to tackle the problem?  Thanks,

---

### Post by coldraven on 2014-04-15
This may not be the same problem as you're having.
My laptop has the ATI X1250 card and uses the open source driver. This card is badly supported and is no good for 3D games etc.
It has a problem with text boxes, quite often the text disappears until I scroll down. I have switched to Unity 2D mode which helps solve the problem.
I don't know if this would affect Xubuntu but it is worth investigating.

---

### Post by monkeybrain20122 on 2014-04-15
I think it is the same problem that plagues kde. If you google it you will find the work around in the kde forums. IIRC you have to edit some css files.

---

### Post by sowdust on 2014-04-16
Coldraven, thank you for the solution but that is not my case.  monkeybrain thank you too for the suggestion but I did search for google and as mentioned I did try to modify the main firefox .css info for the "input" fields but it did not work.

---

### Post by andreas-rabus on 2014-07-11
Just for googlers like me:
Look at [https://wiki.archlinux.org/index.php/firefox#Unreadable_input_fields_with_dark_GTK.2B_themes](https://wiki.archlinux.org/index.php/firefox#Unreadable_input_fields_with_dark_GTK.2B_themes)

In short, for FF 30:

Add or edit ~/.mozilla/firefox/xxxxxxxx.default/chrome/userContent.css 


**Note: **If you want urlbar and searchbar to be white remove both :not css selectors.
 
```

input:not(.urlbar-input):not(.textbox-input) {
    -moz-appearance: none !important;
    background-color: white;
    color: black;
}

#downloads-indicator-counter {
    color: white;
}

textarea {
    -moz-appearance: none !important;
    background-color: white;
    color: black;
}

select {
    -moz-appearance: none !important;
    background-color: white;
    color: black;
}

```

---

