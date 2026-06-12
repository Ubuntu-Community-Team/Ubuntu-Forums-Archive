---
title: "Another gdeklets problem"
date: 2005-03-18
forum: Desktop Environments
---

### Post by DR_K13 on 2005-03-18
So I finally got it installed ( gdesklets ) . I got the shell to work a few times then it errored out anf will not open, I can run via term and this is what I get--
( last part )

```
in /usr/local/lib/gdesklets/shell/plugins/Menu/__init__.py: line 169 set_check_item
in /usr/local/lib/gdesklets/shell/plugins/Menu/__init__.py: line 79 __set_node
[---]/usr/local/lib/gdesklets/shell/plugins/Menu/__init__.py
[---]   74             if (not submenu):
[---]   75                 submenu = gtk.Menu()
[---]   76                 pitem.set_submenu(submenu)
[---]   77
[---]   78         parent, index = self.__get_node(path)
[ERR]>  79         name, nil, children = parent[index]
[---]   80         parent[index] = (name, item, children)
[---]   81         submenu.insert(item, index)
[---]   82
[---]   83
[---]   84
[---]   85     #
``` 



I found the file where  the error is, can someone tell me what to edit?  I know its line #79 but I dont know what to put in its place--


thank you

---

### Post by DR_K13 on 2005-03-18
Anyone?

---

