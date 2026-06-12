---
title: "Bash Expert Needed"
date: 2005-12-08
forum: General Help
---

### Post by M4l3k on 2005-12-08
Hi,

I want to pass a command to a terminal. How to do that?
I tried gnome-terminal | ps -u but it doesn't work.

Tx

M4l3k

---

### Post by 23meg on 2005-12-08
You want to pass it to the gnome-terminal every time it's launched? Try its --command parameter.

---

### Post by M4l3k on 2005-12-08
[QUOTE=23meg]You want to pass it to the gnome-terminal every time it's launched? Try its --command parameter.[/QUOTE]

Hi,

it seems to work but the window closes as soon as the command has been executed. Is there a way to prevent this?

Tx

M4l3k

---

### Post by bsun on 2005-12-08
I don't know actually what you mean but aren't you executing the command through a terminal? 

Actually if you want to redirect all output to another terminal, you can look for something about redirection.

If you have one terminal, then open another one and execute this command in the first terminal.  Still I don't know whether this is what you need. 

ps -au 1> /dev/pts/2

---

### Post by 23meg on 2005-12-08
In your profile options, go to the "Title and Command" tab and choose the "hold the terminal open" option for "when command exits".

---

### Post by M4l3k on 2005-12-08
[QUOTE=bsun]I don't know actually what you mean but aren't you executing the command through a terminal? 

Actually if you want to redirect all output to another terminal, you can look for something about redirection.

If you have one terminal, then open another one and execute this command in the first terminal.  Still I don't know whether this is what you need. 

ps -au 1> /dev/pts/2[/QUOTE]

Hi,

Thanks for your answer. I wasn't that clear in my request. All I want is to run a simulator of mine x times. x being high enough to prevent me from wanting to run  it by hand. I want to automate this procedure by opening automatically a terminal and running the command into it. I want to make a loop as many time as needed and open a terminal each time. I want the opened terminal to remain open so that I can monitor the progress of my simulations (I have some periodic output displayed on the terminal).

Is there a way to do that?

THanks

M4l3k

---

### Post by jwd45244 on 2005-12-08
Google for "expect".  This is a GNU tool that provides means of creating scriptable interactions with applications that don't read from stdin or write to stdout like telnet.  It comes with a tool to watch what you type and create the script.  Using expect-Tk can interact with GUI applications.

---

### Post by jliedeka on 2005-12-08
Or just open a terminal and run

>for j in 1 2 3 4 5 6 7 8 9 10
>do
>your command here
>done

---

