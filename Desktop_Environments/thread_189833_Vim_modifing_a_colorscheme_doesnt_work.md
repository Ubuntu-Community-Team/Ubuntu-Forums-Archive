---
title: "Vim: modifing a colorscheme doesnt work"
date: 2006-06-05
forum: Desktop Environments
---

### Post by lzap on 2006-06-05
Hello,

in all my distros (Mandriva, Gentoo, Suse) this setting of .vimrc:

```
colorscheme desert
hi Normal guifg=White guibg=Black
hi NonText guibg=Black
```

have worked (set the desert scheme with black background - the desert scheme has strange gray background).

In Ubuntu (Dapper Drake) this is not working. Why? :confused:

---

### Post by lzap on 2006-06-05
"Not working" with meaning - its the desert colorscheme set, but with the gray background. It seems the two "highlight" commands are not executed. But when I execute them "by hand" it works.

Ubuntu vim scripts must have some colorscheme clear command after the including of the .vimrc...

---

