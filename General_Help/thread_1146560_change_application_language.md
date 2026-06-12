---
title: "change application language"
date: 2009-05-02
forum: General Help
---

### Post by jARLAXL on 2009-05-02
Hello,

Anybody knows how do i go about changing an application language?
Specifically i want to change the language for the "planner" as i am going to present my results in english. So i want to change the language only of this certain application to english.

Thanks a lot

---

### Post by Jorge_C on 2009-05-02
I think you would launch the app like this from a terminal:
```
LANGUAGE="en" application
```
and you could create a launcher for ease of use if you're going to use it a lot.

---

### Post by jARLAXL on 2009-05-02
Thanks a lot for the answer.
Indeed it starts from the terminal but i had to create a script in order to tell a launcher to start it. In other words this command in not accepted straightly by a launcher. Anyways problem solved. Thank you so much.

---

### Post by jARLAXL on 2009-05-04
Hmm unfortunately planner, eventhough it loads in english, when i resize the gantt chart language changes back.
any ideas about it?
Or should i report it as a bug of this program?

---

### Post by sisco311 on 2009-05-04
```
sudo aptitude install language-pack-en language-support-en
```
(language-support-en is optional)

and try:
```
bash -c "export LANG=en_EN.UTF8 && planner"
```

---

### Post by jARLAXL on 2009-05-04
Thanks you sisco311!
That did the trick!
My honest thanks for the promprt reply too!

---

### Post by sisco311 on 2009-05-04
You're welcome! 

I was in a rush when I wrote my first post. 

language-pack-en provides translation data updates for all supported packages for: English.

language-support-en is a metapackage for English language support for applications.

For more details you can read the description of the packages in Synaptic or type: ```
apt-cache show *package-name*
```
in a terminal. 

*bash -c "command(s)"* runs the command(s) in a bash subshell.


It's useful when you want to create a launcher for a few bash commands. (and you are "lazy" to write a script :) )

The LANG environment variable is used by applications to determine the language to use for error messages and instructions, collating sequences, date formats, and so on.

You set it with the *export LANG=whatever* command.

command1 && command2 means: "execute command2 if command1 succeed"

---

