---
title: "giving a password in a single command line command"
date: 2009-04-19
forum: General Help
---

### Post by fallen seraph on 2009-04-19
So I want to bind to alt+t to open a terminal, execute sudo -i and then for it to enter my password straight away so I'm just presented with a root terminal.

I know it's not the most secure, but security really isn't an issue. 

Also, I've got the hotkey and the sudo -i bit working, I just need to know how to put the password in. Is this possible?

---

### Post by codeseer on 2009-04-19
Why?

---

### Post by fallen seraph on 2009-04-19
For the sake of efficiency. I find myself having to do this often enough to warrant trying to save a few keystrokes in doing so.

---

### Post by ddrichardson on 2009-04-19
Not that I'm advocating this but if security is not a concern (!) and you're doing it all the time, why not enable and login as root?

---

### Post by codeseer on 2009-04-19
sudo visudo

%username ALL=NOPASSWD: /usr/bin/x-term-emulator

gksu /usr/bin/x-terminal-emulator

Do I need to warn you about the implications?

---

### Post by fallen seraph on 2009-04-19
Well, I'm not too worried about security, but all the same that solution is a *bit* much, and also I wouldn't be able to apply it to, say, an ssh command.

I'd still find it preferable to be able to somehow give the password as an argument, or something to that effect?


Indeed, if that's not possible; thank ye for the help nonetheless.

---

### Post by codeseer on 2009-04-19
Try this:

```

#!/bin/bash
sudo -S ls -alt <<EOF
password
EOF

```

---

### Post by fallen seraph on 2009-04-19
Oh wow, that was a lot simpler than I thought. How silly of me not to have tried that!

Anyhow, that's exactly what I was looking for. Thank you very much!

---

