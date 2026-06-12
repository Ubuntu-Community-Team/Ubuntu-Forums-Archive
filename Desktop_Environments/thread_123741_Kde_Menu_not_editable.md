---
title: "Kde Menu not editable"
date: 2006-01-30
forum: Desktop Environments
---

### Post by SilverTab on 2006-01-30
When I start kmenuedit I get:

```

kmenuedit: WARNING: Could not read /home/silvertab/.config/menus/applications-kmenuedit.menu

```


I checked and, home/silvertab/.config/menus/  is empty.... 

I also checked to make sure I have the ownership of the folder..I do..

When I try to save in kmenuedit I get:

```

X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2e00234

```

---

### Post by Adrian on 2006-01-31
Sounds strange. Have you tried launching kmenuedit by right-clicking on the K Menu icon and choosing the "Menu Editor" item?

Will probably not make any difference, but at least it is a suggestion.

---

### Post by DrBair on 2006-02-01
Guess I should read the original post a little better...

Anyway, making another username for testing purposes might help to narrow down the issue.

---

### Post by TristanMike on 2006-02-24
Any ideas, I'm having the same problem, but I don't get that first error. Any help would be greatly appreciated.

Thanx
TM

---

### Post by aysiu on 2006-02-24
[QUOTE=SilverTab]When I start kmenuedit I get:

```

kmenuedit: WARNING: Could not read /home/silvertab/.config/menus/applications-kmenuedit.menu

```


I checked and, home/silvertab/.config/menus/  is empty.... 

I also checked to make sure I have the ownership of the folder..I do..[/quote] I don't know if this helps, but this is what my ~/.config/menus/applications-kmenuedit.menu looks like:```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN" "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">
<Menu>
 <Menu>
  <Name>Applications</Name>
  <Layout>
   <Merge type="files" />
   <Filename>bme.desktop</Filename>
   <Filename>Home.desktop</Filename>
  </Layout>
  <Include>
   <Filename>Home.desktop</Filename>
  </Include>
 </Menu>
</Menu>
```

---

