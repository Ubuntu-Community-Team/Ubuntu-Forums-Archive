---
title: "plot problems"
date: 2010-09-28
forum: Education &amp; Science
---

### Post by yngve on 2010-09-28
hello i've been trying to plott a function, but i've seem to have som problems with the code.
I keep getting the error "evaluating argument list element number"

this is the code

```
%Lab3 plot transfer function.

function [y]=f(w)
y=1./(sqrt((1./(((w.*10.^-6).*i).*(33000.+1.+i.*w.*0.01))).^2)
end

w=50:10:1000000;

[ws, ys]=semilogx (w, y);


plot(ws, ys);
```

and this is the output

octave:1> %Lab3 plot transfer function.
octave:1> 
octave:1> function [y]=f(w)
> y=1./(sqrt((1./(((w.*10.^-6).*i).*(33000.+1.+i.*w.*0.01))).^2)
> end
parse error:

  syntax error

>>> end
      ^

octave:1> 
octave:1> w=50:10:1000000;
octave:2> 
octave:2> [ws, ys]=semilogx (w, y);
error: `y' undefined near line 2 column 23
error: evaluating argument list element number 2
error: evaluating argument list element number 1
octave:2> 
octave:2> 
octave:2> plot(ws, ys);
error: `ws' undefined near line 2 column 6
error: evaluating argument list element number 1
error: evaluating argument list element number 1

---

### Post by aJayRoo on 2010-09-28
Your function definition has unbalanced parentheses, it is missing a right bracket. It probably needs the extra one on the end, but be careful to make sure you put it in the correct place. Also you never called your function f. It would have failed anyway because it wasn't defined properly. You probably need something along the lines of
```
y = f(w);
```
in there somewhere too.

---

### Post by yngve on 2010-09-28
```
[ws, ys]=semilogx (w, y);
```
 seems to be a problem to, because it thinks its a matrix

---

