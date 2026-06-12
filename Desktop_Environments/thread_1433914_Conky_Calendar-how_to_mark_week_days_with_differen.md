---
title: "Conky Calendar-how to mark week days with different color?"
date: 2010-03-19
forum: Desktop Environments
---

### Post by vickoxy on 2010-03-19
Hi,
i wanted only to mark all week days with one different color. Anyone has idea where should i put that color line?

```
${voffset -72}${font andale mono:size=7}${color ffffff}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc -30} /' | sed /" $DJS "/s/" $DJS "/" "'${color 00A9CB}'"$DJS"'${color ffffff}'" "/}${font}

```

---

### Post by vickoxy on 2010-03-21
bump

---

### Post by vickoxy on 2010-03-28
Bump

---

