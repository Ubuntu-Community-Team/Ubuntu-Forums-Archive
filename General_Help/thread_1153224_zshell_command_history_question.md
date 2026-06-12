---
title: "zshell command history question"
date: 2009-05-08
forum: General Help
---

### Post by superdave8000 on 2009-05-08
I can't find a zsh feature I used to love; I was wondering if someone here might know anything about it. The feature: when I type a few letters, and then press "up" for command history, zsh would only bring me the command history that started with the letters I had typed.

Example:
I enter the following three commands:
%mv file1 file2
%cp file2 file3
%vi file3
Now, at a prompt, I type only mv:
%mv
and hit the up arrow. The command history would bring me "mv file1 file2" rather than "vi file3" like other shells.

Does anyone remember this feature? How can I enable it? Or at least, what is it called?

Thanks everyone!

---

### Post by hw-tph on 2009-05-11
Although I admit to being new to zsh, I have this functionality mapped to Alt-P. Ctrl-R triggers history-incremental-search-backward (like the default behaviour of bash - this I have set in my ~/.zshrc). I have no mention of bindkey for Alt-P in my ~/.zshrc so I assume it is a default behaviour or triggered by some default.

Type **bindkey** in the shell to see what keybindings you have. You can edit these and add them to your ~/.zshrc.

---

