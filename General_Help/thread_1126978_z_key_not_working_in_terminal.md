---
title: "z key not working in terminal"
date: 2009-04-15
forum: General Help
---

### Post by Eviltechie on 2009-04-15
For some weird reason the z key no longer works in my terminal. It happened right after I typed bind zope*, instead of find zope*.

---

### Post by mb_webguy on 2009-04-15
```
matt@the-tardis:~$ help bind
bind: bind [-lpvsPVS] [-m keymap] [-f filename] [-q name] [-u name] [-r keyseq] [-x keyseq:shell-command] [keyseq:readline-function or readline-command]
    Bind a key sequence to a Readline function or a macro, or set
    a Readline variable.  The non-option argument syntax is equivalent
    to that found in ~/.inputrc, but must be passed as a single argument:
    bind '"\C-x\C-r": re-read-init-file'.
    bind accepts the following options:
      -m  keymap         Use `keymap' as the keymap for the duration of this
                         command.  Acceptable keymap names are emacs,
                         emacs-standard, emacs-meta, emacs-ctlx, vi, vi-move,
                         vi-command, and vi-insert.
      -l                 List names of functions.
      -P                 List function names and bindings.
      -p                 List functions and bindings in a form that can be
                         reused as input.
      -r  keyseq         Remove the binding for KEYSEQ.
      -x  keyseq:shell-command	Cause SHELL-COMMAND to be executed when
    				KEYSEQ is entered.
      -f  filename       Read key bindings from FILENAME.
      -q  function-name  Query about which keys invoke the named function.
      -u  function-name  Unbind all keys which are bound to the named function.
      -V                 List variable names and values
      -v                 List variable names and values in a form that can
                         be reused as input.
      -S                 List key sequences that invoke macros and their values
      -s                 List key sequences that invoke macros and their values
                         in a form that can be reused as input.
```

Use "bind -p" to list the keybindings.  Locate the keybinding you apparently added inadvertently, and then "bind -r *keyseq*" to remove it.

---

### Post by Eviltechie on 2009-04-15
I think it turned out to be more of a glitch, but I will keep the bind info in mind for the future.

---

