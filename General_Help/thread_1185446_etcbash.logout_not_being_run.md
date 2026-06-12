---
title: "/etc/bash.logout not being run"
date: 2009-06-12
forum: General Help
---

### Post by Causer1984 on 2009-06-12
The title says it all really: /etc/bash.logout is not being run on user logout as defined in "man bash". Tested on 9.04 and 8.04 with no joy. The script is exectutable as 

```

$ bash /etc/bash.logout 
```

so it's not an error in the script itself

~/.bash_logout works as well.

Does anyone know what I'm doing wrong? I am testing using login shells.

---

### Post by deadtom on 2009-06-12
I guess I'm a little confused. So /etc/bash.logout does not work. Does ~/bash_logout work or not work?

---

### Post by Causer1984 on 2009-06-12
Thanks for the reply.

Someone actually solved it for me. Documentation on man bash is wrong. The file that is run on logout is /etc/bash.bash_logout.

Hope that will help someone else in the future!

---

