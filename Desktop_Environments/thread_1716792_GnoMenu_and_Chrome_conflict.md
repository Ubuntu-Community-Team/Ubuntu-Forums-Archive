---
title: "GnoMenu and Chrome conflict"
date: 2011-03-29
forum: Desktop Environments
---

### Post by Canime on 2011-03-29
Hi, I am running GnoMenu recently to add a cool menu to the system bar, but it seems like it is bugging out in some way shape or form because I tried to open chrome and got, "Cannot read preferences, some settings disabled, YES NO"?

---

### Post by Canime on 2011-03-29
I solved the problem with Google chrome, and subsequently had to disable GnoMenu (both because it didn't look good and also it changed the bar too much). To fix it you open terminal and change ownership of two files,

```
cd /home/user/.config/google-chrome
```
```
sudo chown user:user Local State
```
where user:user is the user and group... I just typed my user id twice. Then the same for the 'Preferences' file in the Default folder of google chrome.
```
cd Default
```
```
sudo chown user:user Preferences
```

Restarted the browser and it was fixed :)

---

