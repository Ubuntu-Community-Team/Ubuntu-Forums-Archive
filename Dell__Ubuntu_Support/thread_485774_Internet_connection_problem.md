---
title: "Internet connection problem"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by thaCasper on 2007-06-27
I just installed Ubuntu 7.04, and first i have to say it is the best OS i have ever used. But, i have a problem with the internet connection. I have ADSL connection so i entered this in the terminal:

```
sudo pppoeconf
```

I wrote my user name, pass and said YES to all the questions.

Then i wrote:

```
sudo pon dsl-provider
```

...and my connection was started.

After this i used my browser (mozila) and started opening pages but the network became dead. But i could still talk to my friends on the konebe messenger.

My friend told my that there was some kind of problem so I needed to enter:

```
sudo pkill -9 dhclinet
```

The problem was still there.

Then he told me to do the configuration again, and on the question with the numbers (ex. 452 455 (i am not sure about this numbers)) to say NO.

I did that but still no change. I entered again the code:

```
sudo pkill -9 dhclinet
```

then i started the connection:

```
sudo pon dsl-provider
```

And i had no problem. I had great connection untill this morning when i started the PC, i started the conncetion
```
sudo pon dsl-provider
```

but again there was the problem from before.

I tried the thing from before but nothing helped.

So do you have any idea how can i fix this problem permanently...?

---

### Post by thaCasper on 2007-06-27
Can you please solve this problem? I would really want to get back to ubuntu...

---

