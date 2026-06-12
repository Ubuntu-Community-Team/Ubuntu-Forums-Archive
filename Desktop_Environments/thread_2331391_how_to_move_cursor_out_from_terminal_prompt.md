---
title: "how to move cursor out from terminal prompt"
date: 2016-07-21
forum: Desktop Environments
---

### Post by longfei.zhao on 2016-07-21
Hello to all,

Firstly please allow to me explain more about my problem, so anyone read this don't waste time on something else. Here "terminal prompt",  I mean the line with "user name @ directory $ ". It appears in the bottom of terminal whenever you finish a command. 

Note: My mouse or cursor works perfectly now, and it is just that I want to do something else but I don't find a way online.

What I want:
I want to move cursor back to the command history or previous printed result in the terminal. I don't mean to scroll the screen down to see the history, but really move the cursor there to navigate. 
If you want to ask for the reason: I am using byobu in terminal, which split one terminal to several sub-terminals or windows. If I use "Alt+Up/Down", I can move the cursor into previous printed history, and I can use "/ or ?" like vim after then. This is exactly what I am looking for, except that "Alt+Up/Down" jumps over too much. Since I am searching a lot, I really appreciate a more elegant way to just take the cursor out from prompt.

This may be very easy to configure, but I just cannot find a solution online. Now if I press Up/Down key in the terminal prompt, previous command will come up (incremental history search). This is very helpful. If I can press a short-cut, then press Up/Down key to navigate the cursor on the screen, that will be perfect!

I hope I made my question clear, and someone can give any hint!

:KS

---

### Post by &amp;KyT$0P# on 2016-07-21
I don't know a complete solution, but this should be a start: [http://ascii-table.com/ansi-escape-sequences.php]("http://ascii-table.com/ansi-escape-sequences.php")

Where it says Esc you would type [FONT=Courier New]\033[/FONT]

Example, to move cursor up 4 lines
```
echo -n -e '\033[4A'
```

---

### Post by Habitual on 2016-07-21
Since it sounds like you are searching bash history quite a bit, yes?
I use this in any ~./.bashrc I want to search bash history on:
```

### bind fix for inter and non-interactive bash_history search
iatest=$(expr index "$-" i)
if [[ $iatest > 0 ]]; then bind '"\e[A": history-search-backward'; fi
if [[ $iatest > 0 ]]; then bind '"\e[B": history-search-forward'; fi
```

Using this mechanism, 
If I start retyping part of the command I want and press up, I get command-only <history> for it.
Skipped over it? Press the down key and select. Very clean.

Hope that helps (some one).
Get you some!

---

### Post by DuckHook on 2016-07-21
Welcome to the forums, longfei.zhao

The cursor cannot be "taken out from prompt". You can take a look at all your history by typing:```
history
``` and there are many tricks you can use to invoke specific lines or invoke only lines containing specific values, etc, but the history file is not like a text document; you cannot simply position a cursor over any point in the document. The command line does not work that way. That's why it is called the command *line*. It works only line by line.

---

