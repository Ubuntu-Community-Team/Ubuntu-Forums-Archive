---
title: "longest common sequential subsequence"
date: 2022-12-15
forum: Education &amp; Science
---

### Post by ronakmehta on 2022-12-15
I know how to calculate the lcs of two sequences/strings, however lcs does not need that the subsequence be sequential. I tried it the following way:
```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]function lccs(a, b)[/FONT][/COLOR]
    if a.length == 0 or b.length == 0
        return ""
    possible = []
    if a[0] == b[0]
      possible.push(lcs(a[1:), b[1:])
    possible.push(lcs(a[1:], b))
    possible.push(lcs(a, b[1:)) [COLOR=var(--black-800)][FONT=var(--ff-mono)]    return longest_string(possible)[/FONT][/COLOR]
```

longest string returns the longest string in an array, where s[1:] represents a slice of s beginning with the first character.
I've ran this in javascript within a browser and in golang on a remote server, where I put each call to lccs in its own goroutine, but I have no information about the server's hardware specs, thus I have no notion about the parallelization of these routines. I tried reading from this [site]("https://www.scaler.com/topics/longest-consecutive-subsequence/") but couldn't get it right; can someone help?
It ran far too slowly in each of these circumstances.

---

### Post by TheFu on 2022-12-16
Google found this: [https://rosettacode.org/wiki/Shortest_common_supersequence](https://rosettacode.org/wiki/Shortest_common_supersequence)

I've never had this homework assignment, don't use javascript, nor Go and my code doesn't do this sort of text processing.  I do lots of text conversions for specific outputs, but that's very different than this.  None of my professional work did any text processing.

---

