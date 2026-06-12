---
title: "Firefox broken! (buttons,history,bookmarks,etc) Hardy, latest updates. Please help!!"
date: 2009-03-01
forum: General Help
---

### Post by phalaris on 2009-03-01
My firefox is completely broken and I can't find any info on this problem. All the buttons are greyed out. I can't go back, forward or home. I can't refresh. I can use it to type this message and to post it for example, but once I click 'Submit' I won't be able to go back.
The URL bar is empty and never shows anything.
Bookmarks and history don't work.

Here is a screenshot of what this looks like:
[IMG]http://img223.imageshack.us/img223/2595/screenshotd.png[/IMG]

Any help is really appreciated,

I am using Hardy, latest updates on Dell XPS M1330.

---

### Post by avrilrox on 2009-03-01
Well, If i was you, i would have already reinstalled Firefox.

---

### Post by phalaris on 2009-03-01
> **avrilrox said:**
> Well, If i was you, i would have already reinstalled Firefox.

I did reinstall and it didn't help.
Sorry, I should have mentioned that in the original post.

---

### Post by avrilrox on 2009-03-01
View -> Toolbars -> Customize

Restore default settings

---

### Post by phalaris on 2009-03-01
> **avrilrox said:**
> View -> Toolbars -> Customize

Restore default settings

Tried that too. I actually did try all the obvious steps, and they did not work, otherwise I wouldn't be posting this.

Thanks though, I appreciate the replies

---

### Post by unutbu on 2009-03-01
Have you tried this?
[list]
[*]Quit firefox
[*]Type
```

mv ~/.mozilla ~/.mozilla_20090301
```
or use a file browser to move ~/.mozilla to ~/.mozilla_20090301.
[*]Launch firefox. firefox will notice there is no ~/.mozilla folder, and create you a new one. This will reset firefox to default factory settings.
[/list]
If it works, then we can work on restoring your bookmarks.
If it doesn't work, just type
```
rm -rf ~/.mozilla
mv ~/.mozilla_20090301 ~/.mozilla
```
to restore your current situation.

---

### Post by phalaris on 2009-03-01
> **unutbu said:**
> Have you tried this?
[list]
[*]Quit firefox
[*]Type
```

mv ~/.mozilla ~/.mozilla_20090301
```
or use a file browser to move ~/.mozilla to ~/.mozilla_20090301.
[*]Launch firefox. firefox will notice there is no ~/.mozilla folder, and create you a new one. This will reset firefox to default factory settings.
[/list]
If it works, then we can work on restoring your bookmarks.
If it doesn't work, just type
```
rm -rf ~/.mozilla
mv ~/.mozilla_20090301 ~/.mozilla
```
to restore your current situation.

yay, it worked!
re-installing obviously preserved the settings that's why it didn't work..

epic help, thank you!

---

