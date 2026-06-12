---
title: "lsof -i output from within conky --how??"
date: 2006-01-02
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-01-02
hopefully this is possible and someone will know how to do this? googling did not help as I just could not come up with 'the keyword' :rolleyes: (english not being my natve language, google sometimes is hard)

I want the output of lsof -i -n which looks like this: ```

COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
firefox-b 8509 mehmet   35u  IPv4  37177       TCP XX.XX.XX.XX:40014->XX.XX.XX.XX:www (ESTABLISHED)
firefox-b 8509 mehmet   36u  IPv4  35737       TCP XX.XX.XX.XX:52662->XX.XX.XX.XX:www (ESTABLISHED)
```

to be shown from inside conky like this: ```

COMMAND    NODE NAME
firefox-b TCP XX.XX.XX.XX:40014->XX.XX.XX.XX:www (ESTABLISHED)
firefox-b TCP XX.XX.XX.XX:52662->XX.XX.XX.XX:www (ESTABLISHED)
```

My primary reason is to be able to continously monitor which programs are accessing the net.

I would appreciate any help. Thanks in advance :)

---

