---
title: "Random Quotes on Desktop"
date: 2009-03-16
forum: Desktop Environments
---

### Post by superposition on 2009-03-16
I would like to have a quote from a file displayed on my desktop and have the quote change to a different quote in that file about every minute or so. Is there any programs out there that will do this or is it possible to write a script to do it?

---

### Post by finer recliner on 2009-03-16
install conky which traditionally lets your see system stats overlaid on your desktop (see some of the screenshots on their website), but you could use it call an external script every X number seconds (read the documentation). In the script, use grep, or awk, or sed (or some combination of those tools) to output 1 random line from your library of quotes.

hope this helps point you in the right direction

---

### Post by airtonix on 2009-03-16
fortune is also an option

---

