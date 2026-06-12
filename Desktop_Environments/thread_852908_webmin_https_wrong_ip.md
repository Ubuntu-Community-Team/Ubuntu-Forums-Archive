---
title: "webmin https wrong ip"
date: 2008-07-08
forum: Desktop Environments
---

### Post by mitjab on 2008-07-08
When i am connecting to [http://82.149.25.222:10000](http://82.149.25.222:10000) i get

Error - Bad Request

This web server is running in SSL mode. Try the URL
[https://192.168.123.171:10000/](https://192.168.123.171:10000/) instead.


how to make that adress will be [https://82.149.25.222:10000](https://82.149.25.222:10000) and not local IP

regards

---

### Post by kcnnc on 2008-07-08
Try setting the IP in
Webmin>Webmin Configuration>Ports and Addresses

In addition, 
Webmin>Webmin Configuration>SSL Encryption
Redirect non-SSL requests to SSL mode? **YES**
This should just redirect you to the https address

---

### Post by vasilev on 2010-08-23
i see that the post is old but i have the same problem , 

and .. dont see resolution :)
someone ?

---

