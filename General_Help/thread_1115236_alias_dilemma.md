---
title: "alias dilemma"
date: 2009-04-03
forum: General Help
---

### Post by macjak on 2009-04-03
I created an alias to start the Spike chess engine in xboard. The command works perfectly when I type it on the command line. As soon as I put it between ticks in .bashrc as an alias I get xboard: unrecognized argument -fcp. Here is the command;
xboard -tc 60 -fd ~/engine_two/Spike -fcp ~/engine_two/Spike/spike
This is really baffling me??? I tried creating a .bash_aliases file and did it again with the same results. Thanks for helping!

---

### Post by snova on 2009-04-03
> **macjak said:**
> I created an alias to start the Spike chess engine in xboard. The command works perfectly when I type it on the command line. As soon as I put it between ticks in .bashrc as an alias I get xboard: unrecognized argument -fcp. Here is the command;
xboard -tc 60 -fd ~/engine_two/Spike -fcp ~/engine_two/Spike/spike
This is really baffling me??? I tried creating a .bash_aliases file and did it again with the same results. Thanks for helping!

Ticks? As in backticks (`)? They need to be quotes.

```
alias spike="xboard -tc 60 -fd ~/engine_two/Spike -fcp ~/engine_two/Spike/spike"
```

---

### Post by ibuclaw on 2009-04-03
> **snova said:**
> Ticks? As in backticks (`)? They need to be quotes.

```
alias spike="xboard -tc 60 -fd ~/engine_two/Spike -fcp ~/engine_two/Spike/spike"
```

Or you can put it in a function...

```
function spike { xboard -tc 60 -fd ~/engine_two/Spike -fcp ~/engine_two/Spike/spike; }
```

Regards
Iain

---

### Post by macjak on 2009-04-05
You mean type: alias= function etc.   ?

---

