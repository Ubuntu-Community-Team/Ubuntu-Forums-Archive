---
title: "Difference between .bashrc and .profile file?"
date: 2010-02-22
forum: Desktop Environments
---

### Post by vksingh on 2010-02-22
Hi,
Please help to understand the following:

Difference between .bashrc and .profile file?

Thanks,

Vivek

---

### Post by d3v1150m471c on 2010-02-22
bashrc determines the behavior of a shell while .profile holds the configuration of a shell's profile data

---

### Post by mcduck on 2010-02-22
.bashrc is for Bash only, while .profile is used by other shells as well.

Another important difference is that .profile is used at the time when you log in, be it on a terminal, or into your desktop. So settings in there will apply *always* when youa re logged in. Bashrc on the other hand is executed each time you open a Bash session, for example every time you open a terminal.

Here's an example, I want to add ~/bin to my path, so that I can run programs in that directory without having to type the full apth to them. Since I want that to wosk all the time, even for desktop applications, I need to define that in the .profile file. (doing it in .-bashrc would work for terminal only)

On the other hand I also want to get a fortune every time I open a terminal. So I need to add the comamnd into my .bashrc. (doing it in .profile wouldn't have any noticeable effect when using terminal emulators, since the file wold execute when I log into my desktop, not for each terminal I open).

---

