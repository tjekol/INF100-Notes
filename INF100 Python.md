# INF100 Python

Created: December 5, 2021 9:40 PM
Tags: Programming language

### General stuff

```python
# How to make a variable
# <name of var> = <element in var> (python automatically registers type)
myvar = 204 # myvar is an integer
```

Class/types:

string as `str()` — *tekst*

integer as `int()` — *heltall*

float as `float()` — *desimaltall*

- boolean (bool), `True` / `False`
    
    ```python
    >, <, <=, >=, # større/mindre (lik ) enn
    ==, != ,# er lik, er ulik
    in, not in
    
    if "c" in "cake": # prints if True
    	print("in")
    elif "a" in "cake": # prints if ^False and this True
    	print("in")
    else: # prints is everything above is False
    	print("not found")
    
    bool1 and bool2 # True hvis begge er True
    bool1 or bool2 # True hvis én er True
    not bool1 # True hvis bool1 er False
    
    """ None, 0, 0.0, 0j, (), [], {} er falsy
    1, 1.0, 'x' er truthy """
    ```
    

- Math expressions
    
    `+` — add, concatenate (sette sammen)
    
    `-` — minus, remove
    
    `/` — divides
    
    `//` — integer division, rounds downwards
    
    `%` — modulo,  rest in integer division 
    
    `**` — exponent, ie. $a^2$
    
    `pow(x, y)` == x ** y — $x^y$
    

### Tools

`len()` number of character in string

`max()`, `min()`, `abs()`

`round(value, decimals)` runds float

`input("<question>")` asks user for input

`map(<type>, <list>)` må omgjøres til list/tuple for å printe.

`split(",")` splitter en str til en liste der "," er skille

`" ".join(<liste>)` setter sammen liste til string med " " som skille.

`enumerate(<list>)` for index til variabler i liste

### Code flow/Kodeflyt

- Statements, loops and errors
    
    ```python
    as # samme som å legge noe i en variabel med "=")
    
    while, for # løkker/loops
    
    if, elif (or if), elif not (else not), else # if statements
    	continue, break # starter loop fra start, går ut av loop
    is, is not, in # brukes i statements
    and, or not # boolean algebra
    
    # feilmeldinger
    try, except # catcher feilmeldinger og gjør om
    	except <exception> as <name>
    
    # lage feilmelding
    class <NameOfError>(Exception/<the error>):
    	pass # ignorer/ingenting skjer her
    	raise <NameOfError> # legger hvor feilen skal skje
    
    # eksempel
    xs = ["a", "b", "c"]
    
    try:
        x1 = xs[2]
        x2 = xs[0]
        print(x2 - x1)  # broken, will give error
    
    except IndexError as err:
        print("We caught an IndexError:", err)
    
    except TypeError as err:
        print("We caught a TypeError:", err)
    ```
    
- String, int and float formatting
    
    ```python
    print("One single line") # vanlig string
    print(f"everything is string except this {variable}") # f-string
    	# "\n" gir ny linje
    	# {var:2} formatterer 2 mellom til første verdi
    	# {var:2d} formatterer 2 mellom til siste verdi
    print("""This gives the exact format
    that's in the
    		weird code""")
    
    # alternative to f-string: "," gir mellomrom
    ("everthing in string except this", (variable))
    
    .casefold(), .lower() # gjør str lowercase
    .strip(<character>) # fjerner whitespace og newline(\n)
    
    # text alignment
    # .lstrip(), .rstrip()
    left justify :<, centered :^, right justify :>
    or .ljust(<length>, <character>), .rjust(<width>, <character>)
    # character default is " ", length is from first and to last value
    
    a = "halla"
    b = "hallais"
    c = "hadet"
    
    print(f"{a.ljust(10)} {b} {c:>20}")
    >>halla      hallais                hadet
    
    # format numbers in f-string, {variable:.<number>f}
    a = 1.41
    print(f"{a:.1f}") # gir 1 desimal
    >>1.4
    
    # skjema-format, nb: uten f setter opp format først og så legger inn verdier
    skjema = """Dette vil koste
    {cost:.2f} kr"""
    svar = skjema.format(cost = 19.20)
    print(svar)
    >>Dette vil koste
    >>19.20 kr
    ```
    
- List, tuple, dict, set
    
    ```python
    # hashable brukes som key i dict
    # mutabke = endrelig
    
    list [] — mutable => not hashable
    	print(<list>, end=" ") # prints list items downwards
    	.append(<var/list>), .extend(<var/list>)
    	.remove(<val>) # removes value
    	.pop(<index/val>) # removes the last if no specified index
    	clear() # empties the list
    	del list[<index>] # removes whole list if no specified index
    
    tuple () # immutable => hashable, has to be ONE type
    	# må skrives som (var,) kommaet viser at det er tuple
    
    str "" # immutable => hashable
    
    dict {} # "list" with two values {keys:values}
    	items() is both both keys() and values()
    	dict(zip(<keylist>, <vallist>)) # makes dict of two lists
    	.update({<key>:<value>})
    	.setdefault(<key>, <value>) # legger til key og value
    	.get(<key>, <default>) # gets value  or default of key
    	# give value get key / search by value
    	list(<var>.keys()[list(<var>.values()]).index(<index>)
    	
    	# ways to make dicts
    	dict = {'a': 1, 'b': 2}
    	dict(a = 1, b = 2) # from tuple
    	dict[('a', 1), ('b', 2)] # from list
    	dict(zip(list1, list2)) # from two lists
    
    set {} # hashable, no duplicates
    	.add(<val>), .discard(<val>)
    
    # General
    SLICE[start:stop:step] # index starts on 0
    	# step -1, leses baklengs/reversert
    .sort(), .reverse() # changes list/variable internally
    .sort(revsere=True) # gir store bokstaver først
    	sorted_list = sorted(<list>, key=lambda x:x[<index>]) # sort by index
    	sorted_dict = sorted(<dict>.items(), key=lambda x:x[<index>])
    	# alt: import operator and use key = operator.itemgetter(index)
    .all(), .any()
    
    | == (extend)
    
    # eksempler
    # list comprehension
    newval = [x * <num> for x in mylist]
    new_dict = {i:<v> for i in range(<num>)}
    
    # rid of duplicates in list
    mylist = ["a", "b", "a", "c", "c"]
    mylist = list(dict.fromkeys(mylist)) # make list to dict.keys then list
    print(mylist)
    
    # nested dict
    new = {}
    names = ["george", "gina", "leila"]
    age = [10, 16, 21]
    sex = ["boy", "girl", "girlboss"]
    all_things = list(zip(names, age, gender))
    for nam, a, s in all_things:
    	new.setdefault(nam, [])
    	new[nam] += [a, g] # eller new[n].append([a,g])
    print(new)
    >> {"george": [9:'boy'], "gina": [16:'girl'], "leila": [21:'girlboss']}
    
    # or
    d =[]
    d['dict1'] = {}
    d['dict1']['innerkey'] = 'value'
    d['dict1']['innerkey2'] = 'value2'
    >> {'dict1':{'innerkey':'value', 'innerkey2':'value2'}}
    
    ```
    
- Functions: def, return
    
    ```python
    def animals(*args, **kwargs):
    # *args – uendelig input, **kwargs – uendelig input med key, value(dict)
    
    def name_age(name, age): # def <name of function>(<variables>)
        str(name)
        int(age)
        return (f"{name} er {age} år gammel.") # always return!
    
    print(name_age("Ola",12)) # using the function and giving values
    ```
    
- File handling, csv, pandas
    
    ```python
    # ofte brukt encodings "iso-8859-1"csv, or "utf8" txtfil.
    with open(<"filename">, <'mode'>) as <f>:
    	f.read() - reads the whole file
    	f.readlines() - reads the line for line
    	f.reafline() - reads first line
    
    # alternative way to open file
    f = open(<"filename">, <'mode'>)
    f.write(<"sentence">)
    f.close() # isn't needed
    
    # modes: r(ead), a(ppend) creates and appends, w(rite) creates and overwrites, x(creates)
    
    # CSV
    import csv
    
    with open("filename", newline='') as csvfile: # åpner fil
    	data = csv.reader(csvfile, delimiter(";") # delimiter (kolonneskiller)
    next(csvfile) # overser tittel-rad, kan også skrives header=0 i csv.reader()
    
    # kan skille dataen slik
    name = []
    adr = []
    for <line> in data:
    	name.append(line[<0>])
    	adr.append(line[<2>])
    
    # eller alternativt
    <name>, _, <adr> = data
    # how to use the variables
    for <name>, _, <adr> in data:
    
    # PANDAS
    import pandas as <pd>
    
    <data> = pd.read_csv("airport-codes.csv",
            delimiter = ";",
            encoding = "iso-8859-1",
            header = 0) # skipper header
    
    # skiller data slike med pandas og BARE pandas
    airport_types = data[<"type">] # nyvariabel = datavariabel["kolonnenavn"]
    iata_codes = data[<"iata_code">]
    
    # kan lete etter info lett
    # nyvariabel = data[data["kolonnenavn"] == "ord"]
    fersk = akva[ akva[<'VANNMILJØ'>] == <'FERSKVANN'> ]
    # alt som er ferskvann blir lagt inn i "fersk"
    plt.scatter(x=<fersk['Ø_GEOWGS84'>], y=<fersk['N_GEOWGS84'>], c=<'blue'>, alpha=<0.2>)
    # c(olor), alpha(opacity)
    ```
    
- Libraries: math, numpy, matplotlib
    
    ```python
    import math
    sin(), cos(), sqrt(), pi, log(), floor(), ceil(), comb(k, n)
    # sqrt - square root, floor() runder ned, ceil() runder opp, comb(inations)
    
    # other math lib: decimals, fractions, random, counter
    # random.randint(start index, stop index), random.choice(list)
    
    import numpy as np # also math kinda
    np.array()
    np.arange(start, stop, step) # step er hvor mange verdier fordelt
    np.linspace()
    np.reshape()
    
    xs = [[83, 1, 22], [117, 51, 3], [14, 42, 784]]
    a = np.array(xs)
    print(a)
    >>[[83, 1, 22]
    >>[117, 51, 3]
    >>[14, 42, 784]]
    
    print(a[2,1]) #y, x / rad, kolonne
    >>42
    
    colors: {'b':blue, 'g':green, 'r':red, 'c':cyan, 'm':magenta, 'y':yellow, 'k':black, 'w':white }
    plot styles: {'-':line, '--':stipled line, '-.':line with dots }
    
    import matplotlib as mp
    
    import matplotlib.pylot as plt
    plt.title("title text")
    plt.ylabel("text")
    plt.xlabel("text")
    
    plt.axis(xmin, xmax, ymin, ymax)
    plt.annotate(str, (float, float)) # tekst plottet
    plt.legend(liste) # boks med info
    
    plt.plot(xs,ys)
    plt.scatter(x, y, s=Size, color=Color)
    plt.savefig("filename.png")
    
    plt.show()
    ```