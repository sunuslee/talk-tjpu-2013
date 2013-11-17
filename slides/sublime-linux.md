## Real Life Example

* Goal
  * Re-restructure the document files
  * modify the corresponding file.

* Sounds easy! but how to do it efficiently?


```bash
~ : grep -rno '<section.*slide.*md"' index.html
index.html:39:<section data-markdown="slide-1-welcome.md"
index.html:40:<section data-markdown="slide-2-why-are-you-here.md"
index.html:41:<section data-markdown="slide-3-toc.md"
index.html:42:<section data-markdown="slide-4-linux-0.md"
index.html:43:<section data-markdown="slide-5-linux-1.md"
index.html:44:<section data-markdown="slide-6-linux-2.md"
index.html:45:<section data-markdown="slide-7-python-0.md"
~ : ls
Gruntfile.js                js                          plugin                      slide-2-why-are-you-here.md slide-linux-1.md
LICENSE                     lib                         resources                   slide-3-toc.md              slide-linux-2.md
css                         node_modules                slide-1-welcome.md          		slide-python-0.md
index.html                  package.json                slide-2-about.md            		slide-linux-0.md            test
```


```bash
~ : mkdir slides
~ : mv slide* slides
~ : cd slides
~ : ls
slide-1-welcome.md          slide-2-why-are-you-here.md slide-5-linux-1.md            		slide-7-python-0.md
slide-2-about.md            slide-3-toc.md              slide-4-linux-0.md            		slide-6-linux-2.md

~ : for filename in `ls`; do
~ :    mv $filename "${filename/slide-/}"
~ : done

~ : ls
1-welcome.md          2-why-are-you-here.md 4-linux.md            6-linux.md
2-about.md            3-toc.md              5-linux.md            7-python.md

```


```bash
~ : grep -rno '<section.*slide.*md"' index.html
index.html:39:<section data-markdown="slide-1-welcome.md"
index.html:40:<section data-markdown="slide-2-why-are-you-here.md"
index.html:41:<section data-markdown="slide-3-toc.md"
index.html:42:<section data-markdown="slide-4-linux-0.md"
index.html:43:<section data-markdown="slide-5-linux-1.md"
index.html:44:<section data-markdown="slide-6-linux-2.md"
index.html:45:<section data-markdown="slide-7-python-0.md"
~ : sed -i 1 's/slide-/slides\//' index.html
~ : grep -rno '<section.*slide.*md"' index.html
index.html:39:<section data-markdown="slides/1-welcome.md"
index.html:40:<section data-markdown="slides/2-why-are-you-here.md"
index.html:41:<section data-markdown="slides/3-toc.md"
index.html:42:<section data-markdown="slides/4-linux-0.md"
index.html:43:<section data-markdown="slides/5-linux-1.md"
index.html:44:<section data-markdown="slides/6-linux-2.md"
index.html:45:<section data-markdown="slides/7-python-0.md"
```


##Again, Do NOT Freak Out!!
![noob](resources/noob.png)
