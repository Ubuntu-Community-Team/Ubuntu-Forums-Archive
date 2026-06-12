---
title: "Can't run conky"
date: 2009-04-26
forum: General Help
---

### Post by joshh88 on 2009-04-26
I try to run conky after installing using sudo apt-get install conky I get this error when I try to run. Conky: missing text block in configuration; exiting. I'm confused

---

### Post by VCoolio on 2009-04-26
You need to assign a config file in the command. Copypaste one from the giant thread in the community cafe section or from conky's homepage. Save it for example as ~/conkyconf and then run
conky -c ~/conkyconf
When you just run conky it uses a default config file which is .conkyrc in your homefolder. Apparently it doesn't exist or has nothing after TEXT, which is what conky would display. You can edit configs in your text editor. Just play around with it.

---

