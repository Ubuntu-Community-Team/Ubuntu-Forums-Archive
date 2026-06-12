---
title: "It implies in [https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching"
date: 2022-02-18
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-02-18
It implies in [https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching/](https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching/) that nginx supports range requests only if Cache Slicing is compiled into nginx. 

Does Xubuntu 20.04 nginx support range requests?

---

### Post by TheFu on 2022-02-19
To see the compiled in options,  
```
sudo nginx -V
```

xubuntu doesn't have a specific nginx version. Also, if you care, then you can download the current nginx release code and compile it yourself.

---

