# Character vectors

The last type of R vectors we are going to see in this course are the character vectors. These store values that contain strings, which are anything enclosed within quotation marks. Run the following code to see some examples with strings.

``` R
str_1 <- "Hello world!"
class( str_1 )
str_1

str_2 <- "Hi! This is my second string :)"
str_2 
```

As it happens with numeric/integer/complex vectors, we can have
a character vector with more than one element. For instance,

``` R
fruits <- c( "strawberry", "apple", "orange", "mango" )
fruits 
```

---
###  QUICK EXERCISE 

Which is the function that you can use to find how many values are stored in `fruits`?
Use it and print the result

---
The next part of this tutorial will guide you through some R functions that you can use to deal with character vectors.

## Function `nchar()`
You can type `?nchar` in the terminal to see how it works. Run the next code to see an example of how to use it and try
to understand the output you get

``` R 
nchar( str_2 )
```

###  QUICK EXERCISE

**EX.1.** 
Create two character vectors with the strings you want. Then write a code that prints `TRUE` if the first vector  
has more characters than the second. Otherwise, it should print `FALSE`.

## Functions `toupper()` and `tolower()`
You can type `?toupper` and `?tolower` in the terminal to see how they work. You can then run the code below to see an  example of how they work:

``` R
str_3 <- toupper( str_1 )
str_3
tolower( str_3 )
```

###  QUICK EXERCISE 

**EX.1.**
Convert the vector "fruits" into upper letters and then print the result. Then, convert it back into lower letters and also print the result


There are many examples we could do with REGEX (regular expressions)
# However, we have limited time, so we will just do some examples
# and then you should complete some quick exercises
# Before getting started, you should have read the documentation of
# the following functions: gsub, grep, regexpr


# We are going to create a character vector with a specific 
# string. Afterwards, we are going to use the function gsub to
# find a specific pattern and then replace it by something
# different. Run the code below and try to understand what is 
# happening

# Example 1
str_4 <- c( "pineapple", "tomato", "cheese", "onion" )

str_5 <- gsub( pattern = "pineapple", replacement = "more cheese",
               x = str_4 ) 
str_5

# Example 2
str_6 <- "I like Greek food!"
str_7 <- gsub( pattern = "like", replacement = "love", x = str_6 )
str_7

# Example 3
str_8  <- "We  have   too many             spaces"
str_8
str_9  <- gsub( pattern = "\\s{2,}", replacement = " ", x = str_8 )
str_10 <- gsub( pattern = "have", replacement = "do not have",
               x = str_9 )
str_10

# Example 4
grep( pattern = "pineapple", x = fruits )
grep( pattern = "strawberry", x = fruits)

# ###################
# ---- EXERCISES ----
# ###################

# TIP: go back to the slides in the theory where the REGEX were
#      explained so it can be easier to you to solve the following
#      exercises

# 1. You have the following character vector:
#    str_11 <- c( "cat", "dog", "hamster", "turtle" )
#    Do a regex where either cat or dog are replaced with "hamster"
#
# 2. You have the following character vector:
#    str_12 <- c( "bike", "bilateral", "Mike", "late" )
#    Grep everything that contains the pattern "ike" so you can
#    know in which positions they can be found
#
# 3. Grep everything that ends up with "ate" in str_12 
#
# 4. Grep everything that starts with "bi"
# 
# 5. You have the following character vector:
#    str_13 <- c( "abd98", "aaajlk23", "des2342kk44" )
#    Grep everything that starts with a letter.
#
# 6. Grep everything that contains either "j" or "k" in str_13
# 
# [HARD] 7. Replace any letter in str_13 by a question mark
#           and store the result in a new vector

# ###################
# ---- SOLUTION ----
# ###################

# EX. 1
str_11 <- c( "cat", "dog", "hamster", "turtle" )
gsub( pattern = "dog|cat", replacement = "hamster", x = str_11 )

# EX. 2
str_12 <- c( "bike", "bilateral", "Mike", "late" )
grep( pattern = "ike", x= str_12 )

# EX. 3
grep( pattern = "ate$", x = str_12 )

# EX. 4
grep( pattern = "^bi", x = str_12 )

# EX. 5
str_13 <- c( "abd98", "aaajlk23", "2342kk44des" )
grep( pattern = "^[a-z]", x = str_13 )

# EX. 6
str_14 <- gsub( pattern = "[a-z]", replacement = "\\?", x = str_13 )
str_14 

# ####################
# ----  EXERCISES ----
# ####################

# 1. Create to different numeric vectors and find which values 
#    are different between the two vectors.
# 2. Now find which values are the same.
# 3. Create a third vector that contains the union of 
#    these two vectors.
# 4. Assign the value "6.5789485" to a variable. Find out the class
#    of this vector. Afterwards, round this value to the third digit.
# 5. Now truncate this same value.
# 6. Create a vector named "test1" that contains a sequence of
#    values from 1 to 3 increasing every 0.3 units.
#    What is happening when you use the function floor( test1 )?

# ###################
# ---- SOLUTIONS ----
# ###################

# EX. 1
vec_9  <- c( 1, 4, 5, 1 )
vec_10 <- c( 1, 3, 3, 6 )
setdiff( vec_9, vec_10 )

# EX. 2
intersect( vec_9, vec_10 )

# EX. 3
vec_11 <- union( vec_9, vec_10 )

# EX. 4
vec_12 <- 6.5789485
class( vec_12 )
round( vec_12, digits = 3 )

# EX. 5
trunc( vec_12 )

# EX. 6
test1 <- seq( from = 1, to = 3, by = 0.3 )
floor( test1 )