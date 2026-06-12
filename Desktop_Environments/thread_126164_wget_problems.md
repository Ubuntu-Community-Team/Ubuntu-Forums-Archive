---
title: "wget problems"
date: 2006-02-05
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-05
Alright I wanted to downlaod something from wget. The address was like:
> [www.gijrieis.com/one(1).zip](www.gijrieis.com/one(1).zip)
Well i get an error
> suntax error near unexpected token ('

Is it possible to fix this. Are there other command line prompts to download this link?

---

### Post by bernardfrancois on 2006-02-05
You need to escape the brackets (by preceding them with a backslash). Brackets have a special meaning; what's between them will be executed in a sub-shell (if the brackets are seperated from other characters with spaces, otherwiste you get this 'unexpected token' error).

---

### Post by dickohead on 2006-02-05
you could always try:

wget "http://someurl.com/somefile.extension"

---

### Post by bernardfrancois on 2006-02-06
Which is just another method for escaping...

For anyone who's interested in the full theory behind it, this is an extract from **man bash** (which I see as reccomended reading for every linux user who wants to know how to work with bash)
```

       There are  three  quoting  mechanisms:  the  escape  character,  single
       quotes, and double quotes.

       A  non-quoted  backslash (\) is the escape character.  It preserves the
       literal value of the next character that follows, with the exception of
       <newline>.   If  a  \<newline>  pair  appears, and the backslash is not
       itself quoted, the \<newline> is treated as a line  continuation  (that
       is, it is removed from the input stream and effectively ignored).

       Enclosing  characters  in  single quotes preserves the literal value of
       each character within the quotes.  A single quote may not occur between
       single quotes, even when preceded by a backslash.

       Enclosing  characters  in  double quotes preserves the literal value of
       all characters within the quotes, with the exception of $,  &#8216;,  and  \.
       The  characters  $  and  &#8216;  retain  their special meaning within double
       quotes.  The backslash retains its special meaning only  when  followed
       by one of the following characters: $, &#8216;, ", \, or <newline>.  A double
       quote may be quoted within double quotes by preceding it with  a  back&#8208;
       slash.  When command history is being used, the double quote may not be
       used to quote the history expansion character.

```

---

