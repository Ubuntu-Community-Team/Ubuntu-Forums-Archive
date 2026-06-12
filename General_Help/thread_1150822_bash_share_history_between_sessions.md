---
title: "bash share history between sessions"
date: 2009-05-06
forum: General Help
---

### Post by HadroLepton on 2009-05-06
i want bash to share history between session. the "usual approach" (PROMPT_COMMAND='history -a;history -n;') was no good for me because it messed up the history count. i want to use the bash history expansion (!<number>) so i need stable history numbers.

typically i use history explansion as follows:
1. type history (piped to grep as necessary), press enter
2. look up number of the history entry i want to repeat
3. type "!<number>", press enter

the usual approach will mess up the numbers between step 1 and step 2, so in step 3 i get a wrong history entry expanded.

i tinkered around and got following PROMPT_COMMAND combination which does correct history sharing and also does not mess up the history count.

```

## minimal

PROMPT_COMMAND=''
PROMPT_COMMAND=$PROMPT_COMMAND'history -a;'
PROMPT_COMMAND=$PROMPT_COMMAND'history -c;'
PROMPT_COMMAND=$PROMPT_COMMAND'history -r;'
PROMPT_COMMAND=$PROMPT_COMMAND'history -w;'
PROMPT_COMMAND=$PROMPT_COMMAND'history -c;'
PROMPT_COMMAND=$PROMPT_COMMAND'history -r;'
export PROMPT_COMMAND

export HISTFILE=~/.bash_history.minimal
export HISTCONTROL=ignorespace:erasedups
export HISTFILESIZE=20
export HISTIGNORE='history:h'
export HISTSIZE=20

shopt -s histreedit
shopt -s histverify

alias cd..='cd ..'
alias h='history'

PS1='minimal:\w\n\$ '

```

HISTFILESIZE and HISTSIZE are kept small for testing purposes. i have not tested how the PROMPT_COMMAND behaves when having a huge history size (5000 or 10000).

please comment.

---

### Post by mb_webguy on 2009-05-06
Have you tried the following?```
shopt -s histappend
PROMPT_COMMAND="history -a;$PROMPT_COMMAND"
```

---

### Post by HadroLepton on 2009-05-09
thank you for your answer, but that does not solve my problem in any way.

"shopt -s histappend": this tells bash to, upon exit, append the current history to the history file (instead of overwriting).

"history -a": this command tells bash to append the current history to the history file immediately.

this does not share history between two simultaneously running bash sessions.

what i want is following: open two bash sessions, type command1 in first session, type command2 in second session. now both sessions should have command1 and command2 in theirs history. also i want this without messing up the history count because i like to use the history expansion (!<number>).

---

### Post by intel352 on 2010-11-15
Did you ever find a solution?

---

### Post by HadroLepton on 2010-11-15
i did, sort of. i posted it here: [http://stackoverflow.com/questions/103944/real-time-history-export-amongst-bash-terminal-windows/3055135#3055135](http://stackoverflow.com/questions/103944/real-time-history-export-amongst-bash-terminal-windows/3055135#3055135)

here is a copy of the code:

```

export HISTSIZE=9000
export HISTFILESIZE=$HISTSIZE
export HISTCONTROL=ignorespace:ignoredups

history() {
  _bash_history_sync
  builtin history "$@"
}

_bash_history_sync() {
  builtin history -a         #[1]
  HISTFILESIZE=$HISTFILESIZE #[2]
  builtin history -c         #[3]
  builtin history -r         #[4]
}

export PROMPT_COMMAND=_bash_history_sync

```

follow the link to stackoverflow for more explanation.

---

### Post by nathan.f77 on 2011-01-07
@HadroLepton, thanks for that script, its fantastic.

---

