---
title: "Any ideas how to use aliases with Mutt (please no Url link)"
date: 2009-05-06
forum: General Help
---

### Post by frenchn00b on 2009-05-06
Hello,

I have still no idea how to have a contact book and using aliases with mutt. 
 
like : 
```
echo "salut rober" | mutt -s "msg" robert
```
robert is my alias

---

### Post by andrew.46 on 2009-05-06
Hi frenchn00b,

Easiest way is to write the aliases in your ~/.muttrc file:

```
alias robert \"Robert the Frenchman\" <rob@whatever.com.au>
```

although it is tidier to place all of your aliases in a single file and source them from ~/.muttrc with lines similar to:
```

set alias_file = ~/mail/mutt/mutt_aliases   
source ~/mail/mutt/mutt_aliases 
```  

These are my own settings :-).

Andrew

---

