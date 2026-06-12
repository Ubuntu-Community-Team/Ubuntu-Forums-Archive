---
title: "Looking for MATLAB tip: running sum of a vector"
date: 2009-10-19
forum: Education &amp; Science
---

### Post by lethalfang on 2009-10-19
Is there a faster way to do the following operation?
For a vector, I want a new vector such that, each element in the new vector is the sum of all the elements before it in the old vector. 

I can do it with this loop:

```


old_vector = ones(1, 10); or
old_vector = [ 1 1 1 1 1 1 1 1 1 1]



for i = 1 : length(old_vector)
    new_vector(i) = sum( old_vector( 1:i ) );
end



new_vector = 1 2 3 4 5 6 7 8 9 10


```

But I'm having a bunch of vectors whose lengths are on the order of 10^5, and this loop is really slowing things down. I wonder if there is a fast way to do it.

Thanks in advance!

---

### Post by ahmatti on 2009-10-19
That is called the cumulative sum and Matlab does have a function for it:

```

cumsum(old_vector)

```

That should speed things up considerably :)

---

### Post by lethalfang on 2009-10-19
> **ahmatti said:**
> That is called the cumulative sum and Matlab does have a function for it:

```

cumsum(old_vector)

```

That should speed things up considerably :)

Ohh yeah! Over 100x speed increase!!!

---

