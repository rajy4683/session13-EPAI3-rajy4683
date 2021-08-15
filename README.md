# Generators and Lazy Evaluation

in this repo we will use Generators to read data from a file. Lazy evaluation with generators defers pre-loading large data into memory until evaluation is really required. Simplest example of lazy loading is `range()` which returns a sequence that is never evaluated until needed. Below is an example of generator.

```
def gen_to(n):
    for i in range(n+1):
        yield i
```

Generators support both `iter` and `next` functions hence can be used in `for` loops. However, generators are exhausted and raise `StopIteration` once all elements are yielded. (However, it is possible to create infinite generators too!). To evaluate generators we perform following tasks. 

Implemented code can be found in this [Colab Link](https://colab.research.google.com/drive/1v5FUjxOnrfP3ukTRYBJVdU8E4zxcD7RN?usp=sharing) 

### Task 1
Create a lazy iterator that will return a named tuple of the data in each row. The data types should be appropriate - i.e. if the column is a date, you should be storing dates in the named tuple, if the field is an integer, then it should be stored as an integer, etc.

#### Solution

We pre-define a namedtuple 

```
field_names=['Summons_Number',
 'Plate_ID',
 'Registration_State',
 'Plate_Type',
 'Issue_Date',
 'Violation_Code',
 'Vehicle_Body_Type',
 'Vehicle_Make',
 'Violation_Description']
car_entry_tuple = namedtuple("ViolationEntry",field_names)
```

The generator function is described below:

```
def lazy_file_reader(file_name, mode='r',skip_header=True):
    '''
    Creates a generator function to read from input file_name.
    If skip_header is set, the first line is of the file will be skipped.
    '''
    def convert_datatypes(splitted_list):
        '''
        This function converts datatypes of specific offsets of an input list.
        '''
```

The inner function `convert_datatypes` is responsible for converting each entry to the respective namedtuple.

### Task 2
Calculate the number of violations by car make.

#### Solution

We create a simple function that loops over an input list of namedtuples and sorts it based on the count of violations:

```
def group_violations_by_car_make(full_list: "List"):
    '''
    This function returns a list of vehicles sorted in the descending order of violations count.
    '''
```

## User Details:

Submitted by: Rajesh Y(github: rajy4683)
Email ID: st.hazard@gmail.com
