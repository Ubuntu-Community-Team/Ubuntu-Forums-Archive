---
title: "Ubuntu Gone Beserk"
date: 2009-06-11
forum: General Help
---

### Post by Mike_cog on 2009-06-11
My computer running Hardy 8.04 (originally installed as LTS 6.06) and always kept up to date has started to go mad. When i went to use Firefox to brows the internet it was flickering flat out and i couldn't control it so i opened up System Monitor and that was flickering like mad and hard to read also when i tried to click other tabs it would jump back and i couldn't get it to stay on a tab i did manage to see that the CPU was running between 80 and 100%.
It has all calmed down now but CPU still running average 45%
Can anyone help?
Ta
Mike

---

### Post by x33a on 2009-06-11
maybe some process is hogging the cpu. try finding the process using the system monitor or htop.

---

### Post by colau on 2009-06-11
> **Mike_cog said:**
> My computer running Hardy 8.04 (originally installed as LTS 6.06) and always kept up to date has started to go mad. When i went to use Firefox to brows the internet it was flickering flat out and i couldn't control it so i opened up System Monitor and that was flickering like mad and hard to read also when i tried to click other tabs it would jump back and i couldn't get it to stay on a tab i did manage to see that the CPU was running between 80 and 100%.
It has all calmed down now but CPU still running average 45%
Can anyone help?
Ta
Mike
See which process takes cpu above 40%.
```

sudo aptitude install htop
htop

```
Or
```

top

```
Kill that process.
```

kill -9 <process-id>

```

---

