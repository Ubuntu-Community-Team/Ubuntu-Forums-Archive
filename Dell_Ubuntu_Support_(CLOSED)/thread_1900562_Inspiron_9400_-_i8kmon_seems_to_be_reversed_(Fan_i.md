---
title: "Inspiron 9400 - i8kmon seems to be reversed (Fan issue)"
date: 2011-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by misery11 on 2011-12-26
Hello, 

I have a Dell Inspiron 9400, using "gkrellm" to monitor my GPU and Processor I believe. It displays "GPU C" and "THM" temperatures.

I also use i8kmon to control the fans however it seems to be backwards.
What I mean is that when the processor temp "THM" goes above it's threshold, the GPU fan will be turned on (the left button on the i8kmon GUI).

Beyond this, the GPU doesn't seem to be controlled by the code in the file found here: 

```
sudo gedit /etc/i8mon
```

Meaning that if the GPU temp goes above it's threshold, nothing is turned on. So 2 issues I suppose?

My code is currently set to:

```

set config(0)	{{-1 0}  -1  45  -1  60}
set config(1)	{{-1 1}  37  60  50  70}
set config(2)	{{-1 1}  50  75  60  80}
set config(3)	{{-1 2}  65 120  70 120}
```

Thanks so much for any feedback! :)

---

