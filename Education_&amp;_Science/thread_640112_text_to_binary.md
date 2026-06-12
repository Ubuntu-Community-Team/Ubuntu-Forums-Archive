---
title: "text to binary"
date: 2007-12-13
forum: Education &amp; Science
---

### Post by ricky_cullen on 2007-12-13
hi every one im workin on a sci fair and i was waoundering if any one knew of a program that took any input and turned it into binary, i found a a few that were web based but i will not have a interent  at the sci fai so anyone know any good programs. thanks in advance

---

### Post by talcite on 2007-12-13
I think you might be better off doing it with the calculator... or writing your own program.

It's really simple to make base10 to binary or ASCII to binary programs. Maybe 10 lines of C?

It's also a good beginner's project in programming if you've never tried before.

---

### Post by subs on 2007-12-14
i had written this prog a long time ago.... u will have to run it in java...

> import java.io.*;
public class Binary { 
    public static void main(String[] args) { 
        int N = Integer.parseInt(args[0]);

        // find smallest power of two greater than or equal to N
        int v = 1;
        while (v <= N/2)
            v = v * 2;
  
        // cast out powers of 2 
        while (v > 0) {
           if (N < v) { System.out.print(0);             }
           else       { System.out.print(1);  N = N - v; }
           v = v / 2;
        }

        System.out.println();


   }

}



it converts nos to binary.... to convert letters to binaty... convert them to unicode and then to binary....

---

### Post by liruqi on 2007-12-14
//convert a decimal number to binary reprentation
//import java.io.*;
//import java.lang.*;
public class Binary {
	public static void main(String[] args) {
		System.out.println(Integer.toBinaryString(Integer.parseInt(args[0])));
	}
}
//end of file



//convert a big decimal number to binary reprentation
import java.math.*;
import java.io.*;
import java.util.*;
public class Main
{
	public static void main(String args[])throws Exception
	{
      BufferedReader stdin = new BufferedReader( new InputStreamReader(System.in));
      String str = stdin.readLine();
		BigInteger a = new BigInteger(str);
		System.out.println(a.toString(2));
	}
}//end of file




as for string. I recommend u to use C/C++

---

### Post by subs on 2007-12-15
> **liruqi said:**
> //convert a decimal number to binary reprentation
//import java.io.*;
//import java.lang.*;
public class Binary {
	public static void main(String[] args) {
		System.out.println(Integer.toBinaryString(Integer.parseInt(args[0])));
	}
}
//end of file



//convert a big decimal number to binary reprentation
import java.math.*;
import java.io.*;
import java.util.*;
public class Main
{
	public static void main(String args[])throws Exception
	{
      BufferedReader stdin = new BufferedReader( new InputStreamReader(System.in));
      String str = stdin.readLine();
		BigInteger a = new BigInteger(str);
		System.out.println(a.toString(2));
	}
}//end of file




as for string. I recommend u to use C/C++
i didn know these  libs existed.....

nywayz i prefer a more classical way of shifting between base10 and base2

---

### Post by Zugzwang on 2007-12-15
> **ricky_cullen said:**
> hi every one im workin on a sci fair and i was waoundering if any one knew of a program that took any input and turned it into binary, i found a a few that were web based but i will not have a interent  at the sci fai so anyone know any good programs. thanks in advance

For representing data in binary form, you have to specify some kind of encoding. So far in this thread, you got some examples of converting numbers into binary form (using the "default" encoding). However, you didn't say what kind of input you actually have (maybe text?) and what the encoding should be. Maybe you'd like to tell us which "web based" programs you found so we can figure out what you mean? :)

---

