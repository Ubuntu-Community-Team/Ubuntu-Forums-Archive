---
title: "Is network-admin working properly?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Angel Herranz on 2005-10-22
Sometimes network-admin does not save the configuration correctly.

I run it from a terminal and it broke with a message about an assertion violation (something that had to do with a NULL value returned by gst_xml_current_element).

has anyone noticed problems?

---

### Post by Angel Herranz on 2005-10-23
Here is the message:

```

angel@exodo4:~$ network-admin

** (network-admin:8000): CRITICAL **: gst_xml_element_set_content: assertion `node != NULL' failed

** (network-admin:8000): CRITICAL **: gst_xml_element_set_content: assertion `node != NULL' failed

```

---

### Post by bryan986 on 2005-10-23
I don't get any errors on mine...

---

