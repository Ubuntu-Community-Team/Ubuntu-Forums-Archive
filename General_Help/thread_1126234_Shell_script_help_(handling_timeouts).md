---
title: "Shell script help (handling timeouts)"
date: 2009-04-15
forum: General Help
---

### Post by kpkeerthi on 2009-04-15
Here is a pseudo code of what I need:
```

timeout_seconds='30'

Prompt user for input

If user did not respond within $timeout_seconds
     execute command-x
else
     execute command-y
end-if

exit

```

Can someone please provide the bash equivalent?

---

### Post by KyleBrandt on 2009-04-15
'read -h'

Spoon feeding:
```

#!/bin/bash
timeoutSeconds=10
read -t $timeoutSeconds foo
if [[ -n $foo ]]; then
    echo $foo
else
    echo 'baz'
fi

```

---

### Post by kpkeerthi on 2009-04-15
Thanks for feeding ;)

---

