---
title: "Scribes template error"
date: 2009-05-13
forum: General Help
---

### Post by matmatmat on 2009-05-13
Sorry if this is the wrong place to post this, but when I try to use the templates in scribes it says this:
```

Traceback (most recent call last):
  File "/usr/share/scribes/plugins/Templates/Factory.py", line 95, in __trigger_activated_cb
    self.__templates.append(TemplateProcessor(manager, self.__editor, template))
  File "/usr/share/scribes/plugins/Templates/Processor.py", line 56, in __init__
    self.__init_attributes(manager, editor, template)
  File "/usr/share/scribes/plugins/Templates/Processor.py", line 101, in __init_attributes
    self.__placeholders = get_placeholders(template)
  File "/usr/share/scribes/plugins/Templates/utils.py", line 101, in get_placeholders
    if not_(has_placeholders(string)): return []
  File "/usr/share/scribes/plugins/Templates/utils.py", line 120, in has_placeholders
    if search(placeholder_pattern, string, UNICODE): return True
  File "/usr/lib/python2.6/re.py", line 142, in search
    return _compile(pattern, flags).search(string)
  File "/usr/lib/python2.6/re.py", line 238, in _compile
    raise ValueError('Cannot process flags argument with a compiled pattern')
ValueError: Cannot process flags argument with a compiled pattern

```

---

### Post by matmatmat on 2009-06-09
bump

---

