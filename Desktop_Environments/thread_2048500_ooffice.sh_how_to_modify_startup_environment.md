---
title: "ooffice.sh: how to modify startup environment"
date: 2012-08-26
forum: Desktop Environments
---

### Post by wgw on 2012-08-26
Under ooffice I can normally get accented characters (éàû etc.), but after an update I lost them. I get them back if I start ooffice from bash with ```
env XMODIFIERS='' ooffice -writer %U
```. 

I thought I could modify the ooffice.sh file in /etc/bash_completion.d and add: ```
XMODIFIERS=
export XMODIFIERS
```

but that doesn't work. (Why??) 

What is the best way to make sure XMODIFIERS="" when I run ooffice? I already have that environment setting in my bash.rc. Should I put it somewhere else? I believe I am using ibus, with us international layout. 

I'm still under 10.04 for the moment, but may upgrade soon, when I'm feeling courageous and patient. So this question may be resolved with an upgrade.

---

