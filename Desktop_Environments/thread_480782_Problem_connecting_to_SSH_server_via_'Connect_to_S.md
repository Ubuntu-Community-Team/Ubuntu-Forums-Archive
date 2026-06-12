---
title: "Problem connecting to SSH server via 'Connect to Server'"
date: 2007-06-21
forum: Desktop Environments
---

### Post by Zunino on 2007-06-21
Hello.

I have been unable to connect to a remote SSH server via Gnome's Places->Connect to Server feature, though I have done it several times before with other accounts. I suspect the problem could be related to the fact that my account's username has a special character in it. For some reason, my ISP sets up user SSH accounts using the following scheme (assume 'john' is the username and 'example.com' is the domain):

SSH's username: john@example.com
SSH's host: example.com

Therefore, to log in to that host, one would have to use john@example.com@example.com. I suspect the 'Connect to Server' application is somehow misinterpreting or not knowing how to deal with the username. If I try connecting from the command line, it works. E.g.

ssh john@example.com@example.com

That is what makes me believe there's a problem with the 'Connect to Server' application. I have already tried escaping the '@' character in a couple of different ways, but to no avail.

Does anybody know this to be a bug or have a suggestion of how I might be able to solve it (other than asking my ISP to change their username assignmet policy)?

Thank you very much,

-- 
Ney André de Mello Zunino

---

### Post by jimrz on 2007-06-21
try
```
"john@example.com"@example.com
```
or
```
/john@example.com/@example.com
```

works for funky file names, might work here

---

