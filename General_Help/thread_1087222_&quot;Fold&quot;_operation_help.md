---
title: "&quot;Fold&quot; operation help"
date: 2009-03-04
forum: General Help
---

### Post by 5BallJuggler on 2009-03-04
If i type this in a terminal

```
phil@phil-netbook:~$ fortune | fold -w30
```

I get this,

```
There is an old time toast whi
ch is golden for its beauty.
"When you ascend the hill of p
rosperity may you not meet a f
riend."
		-- Mark Twain
```

Is there a way to "fold" at a word break only?

---

### Post by hexanol on 2009-03-04
I don't know if there's better tool to do so, but you can use

```
$ fortune | tr -s ' ' '\n'
```

:)

---

### Post by 5BallJuggler on 2009-03-04
> **hexanol said:**
> I don't know if there's better tool to do so, but you can use

```
$ fortune | tr -s ' ' '\n'
```

:)

sorry, that breaks at every word, i need to break after 30 or so characters to, i need it to look like this -

```
There is an old time toast 
which is golden for its beauty.
"When you ascend the hill of 
prosperity may you not meet a 
friend."
		-- Mark Twain
```

---

### Post by hexanol on 2009-03-05
Oh sorry, I misunderstood your question.

Well, then, I guess this

```
$ fortune | fold -s -w30
```

is what you are looking for. Next time, take more time to read the man page, it was clearly there ;)

---

### Post by 5BallJuggler on 2009-03-05
> **hexanol said:**
> Oh sorry, I misunderstood your question.

Well, then, I guess this

```
$ fortune | fold -s -w30
```

is what you are looking for. Next time, take more time to read the man page, it was clearly there ;)

I looked at the man pages, but i missed it, don't know why. must be the new glasses.

Thanks very much

---

