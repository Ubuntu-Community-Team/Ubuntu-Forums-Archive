---
title: "Weird zsh/terminal behaviour in out-of-the-box install"
date: 2009-03-24
forum: General Help
---

### Post by holzensp on 2009-03-24
Dear all,

I have changed my user account to use zsh as a default shell. A few things strike me *** odd, though. Most notably (and most annoyingly) tab-completion screws up formatting of my terminal. More specifically, the line being edited is offset by a few characters. As an illustration, this is the starting point:

[IMG]http://www.cs.utwente.nl/~holzensp/shell-1.png[/IMG]

When I now press tab, this happens:

[IMG]http://www.cs.utwente.nl/~holzensp/shell-2.png[/IMG]

As you can see, the line I had so far "ls " is offset. When I delete the line, the cursor doesn't move back to the prompt, but rather to the position of the right-most 'l' in the picture:

[IMG]http://www.cs.utwente.nl/~holzensp/shell-3.png[/IMG]

Potentially related is how long lines are treated. In the following screen shot, you can see that it's not (only) the terminal that is misconfigured, because the problem doesn't occur when using Bash. In both cases, I typed the same line: "This is a test to see how long lines may get before it all turns to garbage"

[IMG]http://www.cs.utwente.nl/~holzensp/shell-4.png[/IMG]

You can see that zsh truncates the line (making the entire prompt disappear). It becomes even more weird when I erase the line by holding backspace:

[IMG]http://www.cs.utwente.nl/~holzensp/shell-5.png[/IMG]

When I erase the line by pressing ^u, the blanking out is slightly more tidy, but the final cursor position is the same.

Another thing that strikes me as odd is that when I log in remotely, using ssh, the backspace key is mapped to delete (erase the character to the *right* of the cursor), but ^h works as normal. This is - also - only the case in zsh. When I start bash, backspace behaves like normal. My .zshrc is as shown below.

If anyone can give me a hint as to what I should do to fix this, I would be much obliged.

Regards,
Philip



```
# Lines configured by zsh-newuser-install
HISTFILE=~/.histfile
HISTSIZE=1000
SAVEHIST=1000
# End of lines configured by zsh-newuser-install
# The following lines were added by compinstall
zstyle :compinstall filename '/home/holzensp/.zshrc'

autoload -Uz compinit
compinit
# End of lines added by compinstall

autoload -U colors
colors
export PROMPT="%n@%m:%B$fg_bold[yellow]%3c$fg[default]> %b"
```

---

### Post by Bachstelze on 2009-03-24
You have a problem in your prompt. If I try to use it on my system, I get the same behaviour, which I don't get with my normal prompt. I'm not very familiar with zsh prompts syntax, though, maybe ask a zsh mailing list?

Your backspace problem is most likely a terminal problem. Which terminal emulator do you use to login through SSH?

---

