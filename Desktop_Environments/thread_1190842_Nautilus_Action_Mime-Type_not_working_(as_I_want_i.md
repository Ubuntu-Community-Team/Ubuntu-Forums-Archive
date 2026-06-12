---
title: "Nautilus Action Mime-Type not working (as I want it to)"
date: 2009-06-18
forum: Desktop Environments
---

### Post by hachel on 2009-06-18
Bonjour,

I have set Nautilus to open executable text-files with the text-editor instead of running it (or prompting me what to do).
So I created a Nautilus-Action with the Nautilus-Action-Configurator that would add an option to the context-menu to execute a file in a terminal.
Under "Conditions" I set mime-type to text/*, so it would only show on text-like files.
It works with basic text-files and python-scripts, but it doesn't show for shell-scripts, even though their mime-type according to "file -i" is "text/x-shellscript".
Any help why this doesn't work?

---

