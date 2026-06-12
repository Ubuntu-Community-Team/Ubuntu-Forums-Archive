---
title: "bash scripting question"
date: 2009-01-12
forum: General Help
---

### Post by imple on 2009-01-12
Hi everyone
I've writien this little bash script:
```
#!/bin/bash
cd /usr/local/sage-3.2.1
./sage
```


Which outputs this:

----------------------------------------------------------------------
| Sage Version 3.2.1, Release Date: 2008-12-01                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
sage: 


If I were in the terminal I could enter "1+2" to get this:

----------------------------------------------------------------------
| Sage Version 3.2.1, Release Date: 2008-12-01                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
sage: 1+2
3

How can I do this automatically from my bash script?

Thanks in advance! :)

---

### Post by heindsight on 2009-01-12
you could put all the input you want to send to the program in a file. Call it sage_input for example.

then you can do
```
./sage < /path/to/sage_input
```

If you also want to append the output to some other file, you could do:

```
./sage < /path/to/sage_input >> /path/to/sage_output
```

---

### Post by hangfire on 2009-01-12
You could also do this.


```
./sage <<END
1+2
END
```

That way, you can keep the input within the script, if desired.

-HF

---

