---
title: "How to display program in terminal tab bar?"
date: 2009-03-12
forum: General Help
---

### Post by transmition on 2009-03-12
I was wondering how I might display the current program in the terminal tab bar as opposed to the current directory.

For example, if I have top running in one tab, and finch in another, I want the tabs to display "top" and "finch" instead of something like "~/" or "~/Documents/"

Any one know how to do this?

---

### Post by kanikilu on 2009-03-12
Someone correct me if I'm wrong, but I believe gnome-terminal (assuming here, since you didn't specify) uses the $PS1 environment variable to dynamically set the title. I don't think there's any way to *dynamically* override that. Even if there was a way to make gnome-terminal look somewhere else for the title, I can't think of any way to get "the currently running process" since there are a lot of concurrently running processes...

You can, of course, manually override the title, but I assumed you were looking for a way to have it set automatically.

For a one-time-use, you can change the title manually by right clicking on the tab and choosing "Set title".

If there are several that you use frequently, you could create new terminal profiles for each and set the title manually (and set the option to keep the intial title), and then just use the "--tab-with-profile=PROFILENAME" option when calling gnome-terminal. Or go to File > Open Tab > and choose the profile.

---

