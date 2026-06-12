---
title: "Evolution compose GUI &quot;mangled&quot; send-to address"
date: 2010-11-11
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-11-11
I have contacts where the details take the following form:
```

"Smith, John" <john.smith@somewhere.com>
"Jones-Brown, Mary" <mary_jones.brown@other.place>

```

When I type part of the name into the Evolution compose gui, I get a list of contacts that match the substring somehow. This part is good.
When I select a contact from the list, Evolution will then populate the Send-To field with something. Often the result is "mangled".

A common error results in something similar to:
```

smith, john john.smith@somewhere.com

```

In general, the quotes and brackets and commas move around and result in strings that cause send errors of various sorts.

What makes this strange is the fact that the addresses shown in the pick list are not mangled. It is only after selection when I tab away from the send-to field into the subject area that the mangling happens.

Merci d'avance,
~~~ 0;-Dan

---

