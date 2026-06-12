---
title: "Starting programs in the background"
date: 2008-10-11
forum: Desktop Environments
---

### Post by PaulW89 on 2008-10-11
Hi,

I want to run some programs at startup.
But I want them to start in a specific order and delayed in some intervals (sleep 5s etc.).

So I created a script like this
```
#!/bin/bash

firefox

sleep 5s
thunderbird

sleep 5s
pidgin
```
and put it into preferences/sessions/startup programs tab/add.

But, of course, now the next program won't start until I close the previous one.

Is there a possibility to start a program in the background, so the script won't stop?

---

### Post by iponeverything on 2008-10-11
> **PaulW89 said:**
> Hi,

I want to run some programs at startup.
But I want them to start in a specific order and delayed in some intervals (sleep 5s etc.).

So I created a script like this
```
#!/bin/bash

firefox

sleep 5s
thunderbird

sleep 5s
pidgin
```
and put it into preferences/sessions/startup programs tab/add.

But, of course, now the next program won't start until I close the previous one.

Is there a possibility to start a program in the background, so the script won't stop?


```

#!/bin/bash
firefox&

sleep 5s
thunderbird&

sleep 5s
pidgin&

```

---

