---
title: "How to make the terminal list more..."
date: 2005-02-20
forum: Desktop Environments
---

### Post by Sophisto on 2005-02-20
Hi! I wonder if anyone knows how to make the terminal to list more than just a certain amount of lines? The reason is that I want it to list all my albums in a certain folder.. (which is over 1000 albums)

Thanks for looking!

---

### Post by valadil on 2005-02-20
As far as I know it varies from terminal to terminal.  I think gnome-terminal (probably ubuntu's default) has a scrollback buffer option in their preferences.

What I'd do instead though is pipe your output.  When you say you want to list all your albums in one folder I assume you mean with ls.  When you do a command in a linux terminal, by default the output is written to the terminal.  With a pipe you can redirect that output into another command.
ls | less

less is a command for viewing text.  You can use it on text files or pipe stuff into it as demonstrated above.  The command I gave you will do ls but output into less where you can scroll up and down through all of the output.

Another option is to redirect into a file:
ls > music.txt
This will write the output of ls into a music.txt file.  This is invaluable for scripting.  While I'm on the topic, using >> instead of > will append data to the file whereas > deletes the contents already in the file first.

Oh and for the record ls -R music/ > music.txt (I have to use -R to do ls recursively because my 1000+ albums are in all sorts of subfolders) gives me this: [http://robotjesus.net/valadil/music.txt](http://robotjesus.net/valadil/music.txt)  It's only 1.4mb of text file!

---

### Post by mendicant on 2005-02-20
I like to use screen to give myself a fixed interface no matter what terminal I'm using, and set the terminal scroll-back buffer to the minimum.  screen allows you to save history to a file, or just scroll back, but has quite a few keyboard commands.

---

