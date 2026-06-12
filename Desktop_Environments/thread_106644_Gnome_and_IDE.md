---
title: "Gnome and IDE"
date: 2005-12-21
forum: Desktop Environments
---

### Post by larry on 2005-12-21
Dear All,
I am starting to program in C++. So far I have been using Gedit and a terminal, but I was advised to use an IDE.
Some people suggested that I should use Kdevelop, but I am using Gnome, so I ended up installing Anjuta 1.2.x.
However, I am already stuck with it (e.g., when I compile and try to execute a simple hello world project [the default new project]), I find out that Anjuta does not find the target executable.
1)Can anyone help me with that? Furthermore, can anyone suggest any good introduction about how to use it for a total beginner? I did not get much out of the Anjuta's site documentation.
2)I often use R for statistical computations.
Can anyone tell me if there is any way to use Anjuta as an IDE for R?

Many thanks and merry Xmas to everybody

Larry

---

### Post by iansyngin on 2005-12-21
can you not compile with gcc file name
then a.out or something like that

---

### Post by larry on 2005-12-21
Surely I can, but I am also sure that as long as the project gets larger, you need something like a IDE (I used to use MS Visual Studio for Fortran in the old days when I was a student).
Cheers

Larry

---

### Post by ijanos on 2005-12-21
I don't remember very well, but i think you need a dev package. Try to run the autogen.sh in your project directory from terminal and it will say what it needs. 

BTW can you detach the toolbars in anjuta and then dock it again in the main window?

---

### Post by Adrian on 2005-12-21
[QUOTE=larry]Some people suggested that I should use Kdevelop, but I am using Gnome, so I ended up installing Anjuta 1.2.x.[/QUOTE]

I know this is not the kind of answer you want, but KDevelop works really good under Gnome. You can create GTK projects as well. I've had more success with KDevelop than Anjuta, even on Gnome.

---

