---
title: "Adding new syntax in gedit for GAMS"
date: 2010-06-05
forum: Desktop Environments
---

### Post by bacalfa on 2010-06-05
Hi, all!

I've been trying to extend gedit with a syntax highlighting capability for GAMS ([http://www.gams.com]("http://www.gams.com/")). I googled about it and could only find it for vim and I didn't quite like it.

Here's what I've done:

(1) I created a file "gams.lang" and placed it in "/usr/share/gtksourceview-2.0/language-specs/"

(2) I created a file "gams.xml" and placed it in "~/.local/share/mime/packages"

(3) I ran the command "update-mime-database ~/.local/share/mime/"

I observed that a test file names "test.gms" was correctly identified as a GAMS source file when I opened it in gedit; however, no highlighting is done. I believe there must an error in my gams.lang file, but I can't find it! Please, help me find where I'm mistaken!

The files are given below:

"gams.lang"
```

<?xml version="1.0" encoding="UTF-8"?>
<!--

 Author: Bruno Abreu Calfa
 Copyright (C) 2010 Bruno Abreu Calfa <bacalfa@gmail.com>

 This library is free software; you can redistribute it and/or
 modify it under the terms of the GNU Library General Public
 License as published by the Free Software Foundation; either
 version 3 of the License, or (at your option) any later version.

 This library is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 Library General Public License for more details.

 You should have received a copy of the GNU Library General Public
 License along with this library; if not, write to the
 Free Software Foundation, Inc., 59 Temple Place - Suite 330,
 Boston, MA 02111-1307, USA.

-->
<language id="gams" _name="GAMS" version="1.0" _section="Sources">
    <metadata>
      <property name="mimetypes">text/x-gams</property>
      <property name="globs">*.gms</property>
      <property name="line-comment-start">*</property>
      <property name="block-comment-start">{</property>
      <property name="block-comment-end">}</property>
    </metadata>

    <styles>
        <style id="comment"           _name="Comment"             map-to="def:comment"/>
        <style id="string"            _name="String"              map-to="def:string"/>
        <style id="preprocessor"      _name="Preprocessor"        map-to="def:preprocessor"/>
        <style id="keyword"           _name="Keyword"             map-to="def:keyword"/>
    </styles>

    <definitions>
        <context id="gams">
            <include>
                <!-- Comments -->
                <context id="comment" style-ref="comment" end-at-line-end="true" class="comment" class-disabled="no-spell-check">
                    <start>\*</start>

                    <include>
                        <context ref="def:in-line-comment"/>
                    </include>
                </context>

                <context id="comment-multiline" style-ref="comment" class="comment" class-disabled="no-spell-check">
                    <start>\{</start>
                    <end>\}</end>
                    <include>
                        <context ref="def:in-comment"/>
                    </include>
                </context>

                <!-- Preprocessor -->
                <define-regex id="preproc-start">\$</define-regex>

                <context id="preprocessor" style-ref="preprocessor" end-at-line-end="true">
                    <start extended="true">
                            \%{preproc-start}
                            (ABORT|BATINCLUDE|CALL|CLEAR|COMMENT|DEFINITION|DOLLAR|DOUBLE|ECHO|EJECT|EOLCOM|ERROR|EXIT|GOTO|HIDDEN|IF|INCLUDE|INLINECOM|KILL|LABEL|LIBINCLUDE|LINES|LOG|MAXCOL|MINCOL|OFFDIGIT|OFFDOLLAR|OFFEMPTY|OFFEND|OFFEOLCOM|OFFEPS|OFFGLOBAL|OFFINCLUDE|OFFINLINE|OFFLISTING|OFFMARGIN|OFFMULTI|OFFNESTCOM|OFFSYMLIST|OFFSYMXREF|OFFTEXT|OFFUELLIST|OFFUELXREF|OFFUPPER|OFFWARNING|ONDIGIT|ONDOLLAR|ONEMPTY|ONEND|ONEOLCOM|ONEPS|ONGLOBAL|ONINCLUDE|ONINLINE|ONLISTING|ONMARGIN|ONMULTI|ONNESTCOM|ONSYMLIST|ONSYMXREF|ONTEXT|ONUELLIST|ONUELXREF|ONUPPER|ONWARNING|PHANTOM|SHIFT|SINGLE|STARS|STITLE|SYSINCLUDE|TITLE|USE205|USE225|USE999)
                            \b
                    </start>
                    <include>
                        <context ref="def:line-continue" ignore-style="true"/>
                        <context ref="string" ignore-style="true"/>
                        <context ref="comment"/>
                        <context ref="comment-multiline"/>
                    </include>
                </context>

                <context id="string" style-ref="string" end-at-line-end="true" class="string" class-disabled="no-spell-check">
                    <start>("|')</start>
                    <end>("|')</end>
                    <include>
                        <context ref="def:line-continue"/>
                    </include>
                </context>

                <context ref="c:decimal"/>

                <context ref="c:octal"/>

                <context ref="c:hexadecimal"/>

                <context ref="c:float"/>

                <context id="gams-keywords" style-ref="keyword" case-sensitive="false">
                    <keyword>ABORT</keyword>
                    <keyword>ACRONYM</keyword>
                    <keyword>ACRONYMS</keyword>
                    <keyword>ALIAS</keyword>
                    <keyword>ALL</keyword>
                    <keyword>AND</keyword>
                    <keyword>ASSIGN</keyword>
                    <keyword>BINARY</keyword>
                    <keyword>CARD</keyword>
                    <keyword>DISPLAY</keyword>
                    <keyword>EPS</keyword>
                    <keyword>EQ</keyword>
                    <keyword>EQUATION</keyword>
                    <keyword>EQUATIONS</keyword>
                    <keyword>GE</keyword>
                    <keyword>GT</keyword>
                    <keyword>INF</keyword>
                    <keyword>INTEGER</keyword>
                    <keyword>LE</keyword>
                    <keyword>LOOP</keyword>
                    <keyword>LT</keyword>
                    <keyword>MAXIMIZING</keyword>
                    <keyword>MINIMIZING</keyword>
                    <keyword>MODEL</keyword>
                    <keyword>MODELS</keyword>
                    <keyword>NA</keyword>
                    <keyword>NE</keyword>
                    <keyword>NEGATIVE</keyword>
                    <keyword>NOT</keyword>
                    <keyword>OPTION</keyword>
                    <keyword>OPTIONS</keyword>
                    <keyword>OR</keyword>
                    <keyword>ORD</keyword>
                    <keyword>PARAMETER</keyword>
                    <keyword>PARAMETERS</keyword>
                    <keyword>POSITIVE</keyword>
                    <keyword>PROD</keyword>
                    <keyword>SCALAR</keyword>
                    <keyword>SCALARS</keyword>
                    <keyword>SET</keyword>
                    <keyword>SETS</keyword>
                    <keyword>SMAX</keyword>
                    <keyword>SMIN</keyword>
                    <keyword>SOS1</keyword>
                    <keyword>SOS2</keyword>
                    <keyword>SUM</keyword>
                    <keyword>SYSTEM</keyword>
                    <keyword>TABLE</keyword>
                    <keyword>USING</keyword>
                    <keyword>VARIABLE</keyword>
                    <keyword>VARIABLES</keyword>
                    <keyword>XOR</keyword>
                    <keyword>YES</keyword>
                    <keyword>REPEAT</keyword>
                    <keyword>UNTIL</keyword>
                    <keyword>WHILE</keyword>
                    <keyword>IF</keyword>
                    <keyword>THEN</keyword>
                    <keyword>ELSE</keyword>
                    <keyword>SEMICONT</keyword>
                    <keyword>SEMIINT</keyword>
                    <keyword>FILE</keyword>
                    <keyword>FILES</keyword>
                    <keyword>PUT</keyword>
                    <keyword>PUTPAGE</keyword>
                    <keyword>PUTTL</keyword>
                    <keyword>PUTCLOSE</keyword>
                    <keyword>FREE</keyword>
                    <keyword>NO</keyword>
                    <keyword>SOLVE</keyword>
                    <keyword>FOR</keyword>
                    <keyword>ELSEIF</keyword>
                    <keyword>ABS</keyword>
                    <keyword>ARCTAN</keyword>
                    <keyword>CEIL</keyword>
                    <keyword>COS</keyword>
                    <keyword>ERROR</keyword>
                    <keyword>EXP</keyword>
                    <keyword>FLOOR</keyword>
                    <keyword>LOG</keyword>
                    <keyword>LOG10</keyword>
                    <keyword>MAP</keyword>
                    <keyword>MAPVAL</keyword>
                    <keyword>MAX</keyword>
                    <keyword>MIN</keyword>
                    <keyword>MOD</keyword>
                    <keyword>NORMAL</keyword>
                    <keyword>POWER</keyword>
                    <keyword>ROUND</keyword>
                    <keyword>SIGN</keyword>
                    <keyword>SIN</keyword>
                    <keyword>SQR</keyword>
                    <keyword>SQRT</keyword>
                    <keyword>TRUNC</keyword>
                    <keyword>UNIFORM</keyword>
                    <keyword>LO</keyword>
                    <keyword>UP</keyword>
                    <keyword>FX</keyword>
                    <keyword>SCALE</keyword>
                    <keyword>PRIOR</keyword>
                    <keyword>PC</keyword>
                    <keyword>PS</keyword>
                    <keyword>PW</keyword>
                    <keyword>TM</keyword>
                    <keyword>BM</keyword>
                    <keyword>CASE</keyword>
                    <keyword>DATE</keyword>
                    <keyword>IFILE</keyword>
                    <keyword>OFILE</keyword>
                    <keyword>PAGE</keyword>
                    <keyword>RDATE</keyword>
                    <keyword>RFILE</keyword>
                    <keyword>RTIME</keyword>
                    <keyword>SFILE</keyword>
                    <keyword>TIME</keyword>
                    <keyword>TITLE</keyword>
                    <keyword>TS</keyword>
                    <keyword>TL</keyword>
                    <keyword>TE</keyword>
                    <keyword>TF</keyword>
                    <keyword>LJ</keyword>
                    <keyword>NJ</keyword>
                    <keyword>SJ</keyword>
                    <keyword>TJ</keyword>
                    <keyword>LW</keyword>
                    <keyword>NW</keyword>
                    <keyword>SW</keyword>
                    <keyword>TW</keyword>
                    <keyword>ND</keyword>
                    <keyword>NR</keyword>
                    <keyword>NZ</keyword>
                    <keyword>CC</keyword>
                    <keyword>HDCC</keyword>
                    <keyword>TLCC</keyword>
                    <keyword>LL</keyword>
                    <keyword>HDLL</keyword>
                    <keyword>TLLL</keyword>
                    <keyword>LP</keyword>
                    <keyword>WS</keyword>
                </context>
            </include>
        </context>
    </definitions>
</language>

```gams.xml
```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="text/x-gams">
        <comment>GAMS source code file</comment>
        <glob pattern="*.gms"/>
    </mime-type>
</mime-info>

```

test.gms
```

SETS
   I   canning plants   / SEATTLE, SAN-DIEGO /
   J   markets          / NEW-YORK, CHICAGO, TOPEKA / ;
PARAMETERS
   A(I)  capacity of plant i in cases
     /    SEATTLE     350
          SAN-DIEGO   600  /
   B(J)  demand at market j in cases
     /    NEW-YORK    325
          CHICAGO     300
          TOPEKA      275  / ;
TABLE D(I,J)  distance in thousands of miles
                NEW-YORK       CHICAGO      TOPEKA
  SEATTLE          2.5           1.7          1.8
  SAN-DIEGO        2.5           1.8          1.4  ;
SCALAR F  freight in dollars per case per thousand miles  /90/ ;
PARAMETER C(I,J)  transport cost in thousands of dollars per case ;
        C(I,J) = F * D(I,J) / 1000 ;
VARIABLES
   X(I,J)  shipment quantities in cases
   Z       total transportation costs in thousands of dollars ;
POSITIVE VARIABLE X ;
EQUATIONS
   COST        define objective function
   SUPPLY(I)   observe supply limit at plant i
   DEMAND(J)   satisfy demand at market j ;
COST ..        Z  =E=  SUM((I,J), C(I,J)*X(I,J)) ;
SUPPLY(I) ..   SUM(J, X(I,J))  =L=  A(I) ;
DEMAND(J) ..   SUM(I, X(I,J))  =G=  B(J) ;
MODEL TRANSPORT /ALL/ ;
SOLVE TRANSPORT USING LP MINIMIZING Z ;

```

---

### Post by sylvaticus on 2011-03-24
hello.. I'm interested as well.. I tried your code.. I can see "GAMS" in the list of syntax highlighter languages, but it does't work.

Did u solve it? (I would be interested also in kate, but gedit is fine as well..)

---

### Post by bacalfa on 2011-03-24
Hi sylvaticus,

A friend of mine just made it partially work. I still don't know why my solution doesn't work. First, delete all those files I was attempting before. Here's the code for the file "gams.lang":

```

<?xml version="1.0" encoding="UTF-8"?>
<!--
 
 Author: Yisu Nie
 
-->
<language id="gams" _name="GAMS" version="2.0" _section="Scripts">
  <metadata>
    <!-- <property name="mimetypes">text/x-ampl;text/plain</property> -->
    <property name="mimetypes"></property>
    <property name="globs">*.gms</property>
    <property name="line-comment-start">\*</property>
  </metadata>
 
  <styles>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="keyword" _name="Keyword" map-to="def:keyword"/>
    <style id="operator" _name="Operator" map-to="def:operator"/>
    <style id="math" _name="math" map-to="def:string"/>
    <style id="logic" _name="logic" map-to="def:special-constant"/>
    <style id="bracket" _name="Bracket" map-to="def:operator"/>
    <style id="floating-point" _name="Floating point number" map-to="def:floating-point"/>
    <style id="decimal" _name="Decimal number" map-to="def:decimal"/>
    <style id="type" _name="Type" map-to="def:type"/>
  </styles>
 
  <default-regex-options case-sensitive="false"/>
 
  <definitions>
    <context id="gams">
      <include>
        <context id="comment" style-ref="comment" end-at-line-end="true">
          <start>\*</start>
          <end>\n</end>
        </context>
 
        <context id="comment-multiline" style-ref="comment" class="comment" class-disabled="no-spell-check">
            <start>/\*</start>
            <end>\*/</end>
            <include>
                <context ref="def:in-comment"/>
            </include>
        </context>
 
        <context id="keyword" style-ref="keyword">
          <keyword>minimize</keyword>
          <keyword>maximize</keyword>
          <keyword>subject to</keyword>
          <keyword>check</keyword>
          <keyword>redeclare</keyword>
      <keyword>print</keyword>
          <keyword>printf</keyword>
      <keyword>option</keyword>
          <keyword>solve</keyword>
          <keyword>reset</keyword>
          <keyword>read</keyword>        
          <keyword>within</keyword>
          <keyword>cross</keyword>
          <keyword>in</keyword>
      <keyword>out</keyword>
          <keyword>from</keyword>
          <keyword>to</keyword>
          <keyword>obj</keyword>
          <keyword>net_in</keyword>
          <keyword>net_out</keyword>
        </context>
 
        <context id="type" style-ref="type">
          <keyword>variable</keyword>
          <keyword>set</keyword>
          <keyword>table</keyword>
          <keyword>parameter</keyword>
          <keyword>variables</keyword>
          <keyword>sets</keyword>
          <keyword>parameters</keyword>
          <keyword>scalar</keyword>
          <keyword>scalars</keyword>
          <keyword>equation</keyword>
          <keyword>equations</keyword>
          <keyword>using</keyword>
        </context>
 
        <context id="math" style-ref="math">
          <keyword>abs</keyword>
          <keyword>acos</keyword>
          <keyword>acosh</keyword>
          <keyword>asin</keyword>
          <keyword>ainsh</keyword>
          <keyword>atan</keyword>
          <keyword>atan2</keyword>
          <keyword>atanh</keyword>
          <keyword>cos</keyword>
          <keyword>cosh</keyword>
          <keyword>exp</keyword>
          <keyword>log</keyword>
          <keyword>log10</keyword>
          <keyword>max</keyword>
          <keyword>min</keyword>
          <keyword>sin</keyword>
          <keyword>sinh</keyword>
          <keyword>sqrt</keyword>
          <keyword>tan</keyword>
          <keyword>tanh</keyword>
          <keyword>sum</keyword>
          <keyword>prod</keyword>
          <keyword>\+</keyword>
          <keyword>-</keyword>
          <keyword>/</keyword>
          <keyword>\*</keyword>
        </context>
 
        <context id="logic" style-ref="logic">
          <keyword>if</keyword>
          <keyword>then</keyword>
          <keyword>else</keyword>
          <keyword>or</keyword>
          <keyword>exists</keyword>
          <keyword>forall</keyword>
          <keyword>for</keyword>
          <keyword>and</keyword>
          <keyword>not</keyword>
          <keyword>in</keyword>
          <keyword>not in</keyword>
        </context>
 
        <context id="operators" style-ref="operator" extend-parent="false">
          <match>[:;\=&lt;&gt;]</match>
        </context>
 
        <context id="brackets" style-ref="bracket" extend-parent="false">
          <match>[\{\}()\[\]]</match>
        </context>
 
        <context id="float" style-ref="floating-point">
          <match extended="true">
            (?&lt;![\w\.])
            ([0-9]+[Ee][+-]?[0-9]+ |
             ([0-9]*\.[0-9]+ | [0-9]+\.[0-9]*)([Ee][+-]?[0-9]+)?)
            (?![\w\.])
          </match>
        </context>
 
        <context id="decimal-number" style-ref="decimal">
          <match extended="true">
            (?&lt;![\w\.])
            [+-]?([1-9][0-9]*|0)
            (?![\w\.])
          </match>
        </context>
 
      </include>
    </context>
 
  </definitions>
</language>

```

Just copy and paste it to "/usr/share/gtksourceview-2.0/language-specs/". Nothing more.

It is not complete in terms of keywords and I haven't had time to fix the regex for the line comment beginning with '*'. But it's a start! Let me know if you can improve it.

---

### Post by sylvaticus on 2011-03-24
Thank you!
I corrected the comment issue, in the sense that now only raws that "start" with a star (== have the star in the first column) are recognised as a comments.

I also removed the C-style /*comments*/ and used instead $ontext/$offtext for multi-line comments (as it is in Gams).

Thank you... :)
   Antonello 

```

<?xml version="1.0" encoding="UTF-8"?>
<!--
 
 Author: Yisu Nie
 
-->
<language id="gams" _name="GAMS" version="2.0" _section="Scripts">
  <metadata>
    <!-- <property name="mimetypes">text/x-ampl;text/plain</property> -->
    <property name="mimetypes"></property>
    <property name="globs">*.gms</property>
    <property name="line-comment-start">\*</property>
  </metadata>
 
  <styles>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="keyword" _name="Keyword" map-to="def:keyword"/>
    <style id="operator" _name="Operator" map-to="def:operator"/>
    <style id="math" _name="math" map-to="def:string"/>
    <style id="logic" _name="logic" map-to="def:special-constant"/>
    <style id="bracket" _name="Bracket" map-to="def:operator"/>
    <style id="floating-point" _name="Floating point number" map-to="def:floating-point"/>
    <style id="decimal" _name="Decimal number" map-to="def:decimal"/>
    <style id="type" _name="Type" map-to="def:type"/>
  </styles>
 
  <default-regex-options case-sensitive="false"/>
 
  <definitions>
    <context id="gams">
      <include>
        <context id="comment" style-ref="comment" end-at-line-end="true">
          <start>^\*</start>
          <end>\n</end>
        </context>
 
        <context id="comment-multiline" style-ref="comment" class="comment" class-disabled="no-spell-check">
            <start>\$ontext</start>
            <end>\$offtext</end>
            <include>
                <context ref="def:in-comment"/>
            </include>
        </context>
 
        <context id="keyword" style-ref="keyword">
          <keyword>minimize</keyword>
          <keyword>maximize</keyword>
          <keyword>subject to</keyword>
          <keyword>check</keyword>
          <keyword>redeclare</keyword>
      <keyword>print</keyword>
          <keyword>printf</keyword>
      <keyword>option</keyword>
          <keyword>solve</keyword>
          <keyword>reset</keyword>
          <keyword>read</keyword>        
          <keyword>within</keyword>
          <keyword>cross</keyword>
          <keyword>in</keyword>
      <keyword>out</keyword>
          <keyword>from</keyword>
          <keyword>to</keyword>
          <keyword>obj</keyword>
          <keyword>net_in</keyword>
          <keyword>net_out</keyword>
        </context>
 
        <context id="type" style-ref="type">
          <keyword>variable</keyword>
          <keyword>set</keyword>
          <keyword>table</keyword>
          <keyword>parameter</keyword>
          <keyword>variables</keyword>
          <keyword>sets</keyword>
          <keyword>parameters</keyword>
          <keyword>scalar</keyword>
          <keyword>scalars</keyword>
          <keyword>equation</keyword>
          <keyword>equations</keyword>
          <keyword>using</keyword>
        </context>
 
        <context id="math" style-ref="math">
          <keyword>abs</keyword>
          <keyword>acos</keyword>
          <keyword>acosh</keyword>
          <keyword>asin</keyword>
          <keyword>ainsh</keyword>
          <keyword>atan</keyword>
          <keyword>atan2</keyword>
          <keyword>atanh</keyword>
          <keyword>cos</keyword>
          <keyword>cosh</keyword>
          <keyword>exp</keyword>
          <keyword>log</keyword>
          <keyword>log10</keyword>
          <keyword>max</keyword>
          <keyword>min</keyword>
          <keyword>sin</keyword>
          <keyword>sinh</keyword>
          <keyword>sqrt</keyword>
          <keyword>tan</keyword>
          <keyword>tanh</keyword>
          <keyword>sum</keyword>
          <keyword>prod</keyword>
          <keyword>\+</keyword>
          <keyword>-</keyword>
          <keyword>/</keyword>
          <keyword>\*</keyword>
        </context>
 
        <context id="logic" style-ref="logic">
          <keyword>if</keyword>
          <keyword>then</keyword>
          <keyword>else</keyword>
          <keyword>or</keyword>
          <keyword>exists</keyword>
          <keyword>forall</keyword>
          <keyword>for</keyword>
          <keyword>and</keyword>
          <keyword>not</keyword>
          <keyword>in</keyword>
          <keyword>not in</keyword>
        </context>
 
        <context id="operators" style-ref="operator" extend-parent="false">
          <match>[:;\=&lt;&gt;]</match>
        </context>
 
        <context id="brackets" style-ref="bracket" extend-parent="false">
          <match>[\{\}()\[\]]</match>
        </context>
 
        <context id="float" style-ref="floating-point">
          <match extended="true">
            (?&lt;![\w\.])
            ([0-9]+[Ee][+-]?[0-9]+ |
             ([0-9]*\.[0-9]+ | [0-9]+\.[0-9]*)([Ee][+-]?[0-9]+)?)
            (?![\w\.])
          </match>
        </context>
 
        <context id="decimal-number" style-ref="decimal">
          <match extended="true">
            (?&lt;![\w\.])
            [+-]?([1-9][0-9]*|0)
            (?![\w\.])
          </match>
        </context>
 
      </include>
    </context>
 
  </definitions>
</language>

```

---

### Post by bacalfa on 2011-03-25
Thanks a lot, Antonello!

That's why I love Ubuntu and its community!

Now we only have to figure out how to change the syntax color of the explanatory text for variables, sets, tables, parameters, equations... :(

Take care!


Bruno

---

### Post by Veneno on 2011-05-22
Sorry to stir up an old thread... But I'd like to know if anyone took this any further. I'm working with GAMS right now and I prefer gedit to emacs, since I've worked more with the previous.

Thanks anyway!

---

### Post by bluesboba on 2012-04-13
I need this as well!

---

### Post by nicklas898haohao on 2012-04-13
But I'd like to know if anyone took this any further. I'm working with GAMS right now and I prefer gedit to emacs[IMG]http://**************************/g.gif[/IMG]

---

