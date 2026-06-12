---
title: "csh trouble"
date: 2009-06-11
forum: General Help
---

### Post by perhaugaard on 2009-06-11
Dear users,

I do not know if this is the right place to submit this question but I will try.

I have a small program in csh that should help do some calculations. Here is the part of my script with does not work as expected:

cat <<_EOF_ >! $prg
BEGIN { 
	n=0;
	dftot=0.0;
	dflim=1000;
}
{
 df=(double)\$1;
 n=n+1;
 dftot=dftot+df;
 if (dftot/n>2.0) dflim=df;
}
END { printf dflim;
    }
_EOF_
cat $prg >! code.prg

cat data.dat | sort -n -r | awk -f $prg >$dflim
cat $dflim >! data.dflim

data.dat contains a series of data which is to be evaluated by $prg and sent as output to data.dflim. BUT nothing seem to happen and the only data written to data.dflim is 1000. I was expecting something else.

Does anyone have any idea of what can be wrong? 


Any help is appreciated

/Per

---

### Post by jonobr on 2009-06-11
Hello


I would recommend going to the programming section and posting there.

Those guys over there rock, and will probably have a response out before you even post.

They will also reduce the code to so few characters that the the answer will only contain one letter

Also, more importantly, those posts move a lot slower in the programming section then in the general section, so you have a better chance of the right people seeing it

Ciao!

---

### Post by perhaugaard on 2009-06-12
Thnx m8. I will post it there :)


/Per

---

