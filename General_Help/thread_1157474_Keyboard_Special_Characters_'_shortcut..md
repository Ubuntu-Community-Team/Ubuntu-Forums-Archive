---
title: "Keyboard Special Characters ' shortcut."
date: 2009-05-12
forum: General Help
---

### Post by MXIIA on 2009-05-12
I'm currently running Ubuntu 9.04.
I'm currently enrolled in a Spanish class online, and in order to type certain characters such as the é or ñ, I had to enable "USA International (with deadkeys)." 

This works fine for the task at hand, but the problem arises when it tries to use something outside of the "alt" key's functions. It has these annoying shortcuts. In fact, 2 of them came up just typing up this little blurb. They are centered around the apostrophe key (to the right of the left enter key). When typing words that have an apostrophe in them, such as "I'm" or "key's" it wants to put the apostrophe over the letter after it. Without using the non-breaking space that I had to use to escape this annoying shortcut, the results would  have been "I&#7743;" and "key&#347;." 

The second annoying shortcut, I actually discovered while typing this up. It is also originating from the same apostrophe key that the above shortcut was caused by. When typing a quote (") you must use the non-breaking space in order to actually type the quote. After messing around with this shortcut, I discovered that it is used to type characters such as the "Ü" and the "Ë" but these will rarely be typed, from my experience. These could also easily be used with the "alt" key and another key, such as the "super" (or Windows) key. 

My question is: is it possible for me to disable this very aggrivating shortcut?

Thank you for your time, 
MXIIA

---

### Post by pro003 on 2009-05-12
i think your answer might be here:

[https://answers.launchpad.net/ubuntu/+question/52142](https://answers.launchpad.net/ubuntu/+question/52142)

---

### Post by MXIIA on 2009-05-12
It answers my question to a lesser extent, as ChrisDodd said in his final comment, the solution was specific to his keyboard layout, and does not work on mine. I have a "Generic 105-key (Intl) PC" layout. ChrisDodd did not specify what layout he has on his keyboard.

---

### Post by MXIIA on 2009-05-12
Oh, if it helps, I do indeed have SKIM installed, although I do not think the solution lies in that.

---

### Post by CatKiller on 2009-05-13
> **MXIIA said:**
> I have a "Generic 105-key (Intl) PC" layout.

Me too, and I didn't need to add dead keys. I can get those characters with the Compose key, which you can set in the keyboard preferences. For example, ñ can be generated with (Shift-Compose)-~-n. Without using the Compose key, normal characters display as they should.

---

### Post by fballem on 2009-05-13
> **MXIIA said:**
> I'm currently running Ubuntu 9.04.
I'm currently enrolled in a Spanish class online, and in order to type certain characters such as the é or ñ, I had to enable "USA International (with deadkeys)." 

This works fine for the task at hand, but the problem arises when it tries to use something outside of the "alt" key's functions. It has these annoying shortcuts. In fact, 2 of them came up just typing up this little blurb. They are centered around the apostrophe key (to the right of the left enter key). When typing words that have an apostrophe in them, such as "I'm" or "key's" it wants to put the apostrophe over the letter after it. Without using the non-breaking space that I had to use to escape this annoying shortcut, the results would  have been "I&#7743;" and "key&#347;." 

The second annoying shortcut, I actually discovered while typing this up. It is also originating from the same apostrophe key that the above shortcut was caused by. When typing a quote (") you must use the non-breaking space in order to actually type the quote. After messing around with this shortcut, I discovered that it is used to type characters such as the "Ü" and the "Ë" but these will rarely be typed, from my experience. These could also easily be used with the "alt" key and another key, such as the "super" (or Windows) key. 

My question is: is it possible for me to disable this very aggrivating shortcut?

Thank you for your time, 
MXIIA

I have to work in three languages - English, French, and Portuguese. Like you, I hate having the accented keys show up when I'm typing in English.

My solution is relatively simple:

[LIST=1]
[*]If you add a keyboard indicator to the panel, then you can easily switch keyboard layouts when required. To enable this:
[LIST=2]
[*]Right-click on the top panel (assuming you're using GNOME). This will produce a menu.
[*]From the menu, select 'Add to Panel'.
[*]Scroll down the list of applets until you find the keyboard indicator applet. Highlight it, then click the Add button (see Screenshot-Add to Panel)).
[*]You should now see the keyboard indicator on the top panel. You can move this to a convenient location by right-clicking and then selecting the Move option.
[*]Once you have it in a convenient place, you can lock it by right-clicking and then selecting the Lock to Panel option.
[/LIST]
[*]Once you have the keyboard indicator, right-click on the keyboard indicator, then select Keyboard Preferences from the menu. This will display a tabbed menu.
[LIST=2]
[*]Select the Layouts tab from the tabbed menu (see Screenshot-Keyboard Preferences).
[*]Select the Add button. This will allow you to add additional layouts.
[*]I have provided a screenshot that shows how to add the US International keyboard, but the same method can be used to setup the US Keyboard (the one without the accents). See Screenshot-Choose a Layout.
[*]Once you have the correct layout selected, click the Add button and you will return to the Keyboard Preferences.
[*]Identify one of the keyboards as your 'default' layout. In your case, you will probably identify the US keyboard as the default. (see the Screenshot-Keyboard Preferences).
[*]If you wish, you may apply this system-wide so that the same keyboard options will be available to all users, including root (which you access through sudo commands).
[*]When you are done, select the close button.
[/LIST]
[*]To use the keyboard indicator, just click on it and it will cycle through. In my case, the indicator will show USA when I'm using a normal US keyboard and USA2 when I'm using the US International Keyboard.
[/LIST]

Hope this helps,

---

### Post by MXIIA on 2009-05-13
fballem, that is essentially what I am looking for. Although, a setting to disable the *magic accent* would be better, I believe your solution works quite nicely.

Thank you!

---

### Post by fballem on 2009-05-13
> **MXIIA said:**
> fballem, that is essentially what I am looking for. Although, a setting to disable the *magic accent* would be better, I believe your solution works quite nicely.

Thank you!

You're welcome. Glad I could help.

---

