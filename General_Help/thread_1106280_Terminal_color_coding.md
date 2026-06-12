---
title: "Terminal color coding"
date: 2009-03-25
forum: General Help
---

### Post by djslothario on 2009-03-25
Hi all,

I'm trying to get color coding to work in my terminal - you know, having directories different colors than files, and so on, and enable code highlighting when I'm using vi. How do I do that? Briefly playing with the color settings in the terminal menu doesn't fix it. Thoughts?

Danny

---

### Post by snova on 2009-03-25
> **djslothario said:**
> I'm trying to get color coding to work in my terminal - you know, having directories different colors than files, and so on, ...

With the ls command, you need to specify the --color=auto option. To make it the default, create an alias for it. Add it to the end of ~/.bashrc:

```
alias ls="ls --color=auto"
```

Then it will be run with that option every time.

> ... and enable code highlighting when I'm using vi.

I'm not quite sure about that one, but I believe you have to add this line to ~/.vimrc:

```
:syntax enable
```

---

