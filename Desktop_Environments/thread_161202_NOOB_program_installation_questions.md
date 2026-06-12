---
title: "NOOB program installation questions"
date: 2006-04-16
forum: Desktop Environments
---

### Post by drfox on 2006-04-16
How do I install a deb package that I've downloaded? I need to try to set up a Brother MFC scanner.

How do I install a sh package that I've downloaded? I've downloaded MoneyDance and I've tried opening it with Bash. It wants to install into usr/local/moneydance, but I get an error that I have no write priveleges in that directory. When I install as Root, I can't find the program when I log in as a regular user.

Where should programs go when they're installed? \usr\share\program_name? somewhere else?

Larry

---

### Post by Ramses de Norre on 2006-04-16
sudo dpkg -i /path/to/file.deb

---

