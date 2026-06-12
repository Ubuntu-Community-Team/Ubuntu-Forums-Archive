---
title: "Vi and cursor position"
date: 2006-07-04
forum: Desktop Environments
---

### Post by babis85 on 2006-07-04
Hello all, i have a problem with vi which is getting in(on) - i am not sure for the collocation, please correct me -  my nerves. When i finish editing a file, save it and close it, the next time i will open it i want the cursor to start from where i finished the last time. This does happen only if i edit the file with sudo. I have copied the file /usr/share/vim/vim64/vimrc_example to my home directory named .vimrc. What can i do next to solve this? Thanks...

---

### Post by yabbadabbadont on 2006-07-04
Make sure that there is a valid "viminfo" option configured in your .vimrc file.  It is what keeps track of the files you edited, where you were in them, and the contents of named cut buffers.

---

### Post by babis85 on 2006-07-04
There is no such option in my .vimrc file, but you gave me the idea and i saw the light. In my home directory it did exist a file .viminfo but i hadn's permission to write. I change owner and worked good. Thanks

---

### Post by Joe Momma on 2007-06-05
Thanks guy, I was having the same problem and couldn't figure it out.

I never had this problem on previous versions, but on a fresh feisty install .viminfo was owned by root.

Bug?

---

### Post by AnRa on 2007-06-05
That happens when you start vim using "sudo vim" and the file .viminfo hasn't been created already.

---

### Post by x1a4 on 2007-06-05
Hi,

Is having a writable .viminfo file really the only thing you need to get vim to remember the cursor position?  I'm asking because I needed to add some fancy code in my .vimrc before vim started remembering cursor position.

---

### Post by Crash80 on 2007-06-08
> **x1a4 said:**
> Hi,

Is having a writable .viminfo file really the only thing you need to get vim to remember the cursor position?  I'm asking because I needed to add some fancy code in my .vimrc before vim started remembering cursor position.

for me changing permissions didnt resolve the problem. which fancy code did you put into your .vimrc?

---

### Post by x1a4 on 2007-06-08
> **Crash80 said:**
> which fancy code did you put into your .vimrc?

```

if has("autocmd")
[indent]
     autocmd BufReadPost *
      \ if line("'\"") > 0 && line("'\"") <= line("$") |
      \   exe "normal g`\"" |
      \ endif
[/indent]
endif

```

---

### Post by x1a4 on 2007-06-08
> **AnRa said:**
> That happens when you start vim using "sudo vim" and the file .viminfo hasn't been created already.

If that's happening on your system, that means your umask is set incorrectly.  I have mine set to 0022.

---

### Post by AnRa on 2007-06-09
> **x1a4 said:**
> If that's happening on your system, that means your umask is set incorrectly.  I have mine set to 0022.

My umask is set 0022 and I've tried this in two different PCs. The umask affects only the file permissions and not the ownership of them.

---

### Post by x1a4 on 2007-07-01
> **AnRa said:**
> My umask is set 0022 and I've tried this in two different PCs. The umask affects only the file permissions and not the ownership of them.

The first digit sets uid(4), gid(2) and sticky(1) bits, and the following three set the permissions for owner, group and other respectively--same as in chmod.  

For example: to set gid and sticky use 3 (2+1), to set uid and gid use 6 (4+2).

---

### Post by stuartmacgregor on 2008-06-16
Thanks for the tip - adding the suggested to .vimrc worked a treat. vi not going to the previous position had been annoying me ever since I moved to ubuntu.

---

