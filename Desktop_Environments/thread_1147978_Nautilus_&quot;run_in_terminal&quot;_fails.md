---
title: "Nautilus &quot;run in terminal&quot; fails"
date: 2009-05-03
forum: Desktop Environments
---

### Post by etitor on 2009-05-03
Hi friends. Under Ubuntu 8.10 and before that, clicking on a file marked as executable (e.g., a perl script) made Nautilus offer 4 options: run file in terminal, open, cancel, run.

After upgrading to Ubuntu 9.04, Nautilus offers those 4 options, but when the first one is chosen (run in terminal) a quick flash of a terminal appears and disappears without running the script.

An error message appears very quickly in the terminal: "file not found /usr/bin/perl". I think this is related to the first line of any perl script, known as shebang: #!/usr/bin/perl.

Of course what the error message states is not true: /usr/bin/perl does exist.

The same script works OK when launched from the terminal (i.e., not using Nautilus).

Has anyone experienced trouble executing a script through popup menus in Nautilus?

---

### Post by etitor on 2009-05-10
> **etitor said:**
> Hi friends. Under Ubuntu 8.10 and before that, clicking on a file marked as executable (e.g., a perl script) made Nautilus offer 4 options: run file in terminal, open, cancel, run.

After upgrading to Ubuntu 9.04, Nautilus offers those 4 options, but when the first one is chosen (run in terminal) a quick flash of a terminal appears and disappears without running the script.

An error message appears very quickly in the terminal: "file not found /usr/bin/perl". I think this is related to the first line of any perl script, known as shebang: #!/usr/bin/perl.

Of course what the error message states is not true: /usr/bin/perl does exist.

The same script works OK when launched from the terminal (i.e., not using Nautilus).

Has anyone experienced trouble executing a script through popup menus in Nautilus?

I solved this out by myself and thought it would be useful to share.

Just be sure no BOM (byte order mark) exists at the very beginning of your script's file. The BOM is added by some text editors, notably Geany, but prevents the script from being run from Nautilus since the BOM interferes with the shebang line.

---

