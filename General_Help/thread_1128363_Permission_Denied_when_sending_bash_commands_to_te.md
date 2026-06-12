---
title: "Permission Denied when sending bash commands to text"
date: 2009-04-17
forum: General Help
---

### Post by Kapurnicus on 2009-04-17
I was trying to modify my /etc/issue file to include a clear screen before hand. From what I know I can send one like this

"sudo clear > /etc/issue"

but im getting permission denied... I'm root, why is my permission denied?! 
If anyone can clear this up I'll appreciate it. It should be simple, but I'm confused.

---

### Post by Kapurnicus on 2009-04-17
Someone actually answered this just two hours ago, guess I wasnt searching for the right stuff :)  the answer is anything after your command is not executed as root.

clear | sudo tee /etc/issue

Thanks for the help guys. Seems like a good place for questions

---

### Post by KeyserSoze93 on 2009-04-17
Because the > operator is recognised by your shell, not the root privalidged program you called. The simplest way to do it is probably with su:
```
su -c "clear > /etc/issue"
```

However, AFAIK /etc/issue is a text file, and is interpreted as such, whereas clear does it's work using escape sequences for the terminal, not by printing 24 blank lines.

If you always use a 24 line terminal, you may simply want to run:
```
for i in $(seq 1 24); do su -c "echo >> /etc/issue"; done
```

---

### Post by Bachstelze on 2009-04-17
> **KeyserSoze93 said:**
> Because the > operator is recognised by your shell, not the root privalidged program you called. The simplest way to do it is probably with su:

[font="monospace"]su[/font] will not work in Ubuntu by default. The correct way to remove all text from a file in Ubuntu is

```
echo -n | sudo tee /etc/issue
```

---

