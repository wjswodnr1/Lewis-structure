# Lewis-structure
#Lewis structure
from tkinter import *
from tkinter import messagebox
element = [None, 'H','He','Li', 'Be', 'B', 'C', 'N', 'O', 'F', 'Ne', 'Na', 'Mg', 'Al', 'Si', 'P', 'S', 'Cl', 'Ar', 'K', 'Ca', 'Sc', 'Ti', 'V', 'Cr', 'Mn', 'Fe', 'Co', 'Ni', 'Cu', 'Zn', 'Ga', 'Ge', 'As', 'Se', 'Br', 'Kr', 'Rb', 'Sr', 'Y', 'Zr', 'Nb', 'Mo', 'Tc', 'Ru', 'Rh', 'Pd', 'Ag', 'Cd', 'In', 'Sn', 'Sb', 'Te', 'I', 'Xe', 'Cs', 'Ba', 'La', 'Ce', 'Pr', 'Nd', 'Pm', 'Sm', 'Eu', 'Gd', 'Tb', 'Dy', 'Ho', 'Er', 'Tm', 'Yb', 'Lu', 'Hf', 'Ta', 'W', 'Re', 'Os', 'Ir', 'Pt', 'Au', 'Hg', 'Tl', 'Pb', 'Bi', 'Po', 'At', 'Rn', 'Fr', 'Ra', 'Ac', 'Th', 'Pa', 'U', 'Np', 'Pu', 'Am', 'Cm', 'Bk', 'Cf', 'Es', 'Fm', 'Md', 'No', 'Lr', 'Rf', 'Db', 'Sg', 'Bh', 'Hs', 'Mt', 'Ds', 'Rg', 'Cn', 'Nh', 'Fl', 'Mc', 'Lv', 'Ts', 'Og']
electronegativity = [None, 2.20, 0, 0.98, 1.57, 2.04, 2.55, 3.04, 3.44, 3.98, 0, 0.93, 1.31, 1.61, 1.90, 2.19, 2.58, 3.16, 0, 0.82, 1.00, 1.36, 1.54, 1.63, 1.66, 1.55, 1.83, 1.88, 1.91, 1.90, 1.65, 1.81, 2.01, 2.18, 2.55, 2.96, 3.00, 0.82, 0.95, 1.22, 1.33, 1.6, 2.16, 1.9, 2.2, 2.28, 2.20, 1.93, 1.69, 1.78, 1.96, 2.05, 2.1, 2.66, 2.6, 0.79, 0.89, 1.1, 1.12, 1.13, 1.14, 1.13, 1.17, 1.2, 1.2, 1.1, 1.22, 1.23, 1.24, 1.25, 1.1, 1.27, 1.3, 1.5, 2.36, 1.9, 2.2, 2.20, 2.28, 2.54, 2.00, 1.62, 2.33, 2.02, 2.0, 2.2, 0, 0.7, 0.9, 1.1, 1.3, 1.5, 1.38, 1.36, 1.28, 1.13, 1.28, 1.3, 1.3 ,1.3, 1.3, 1.3, 1.3, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]        
class Element:
    def __init__(self, e_number, EN):
        self.EN = EN
        self.e_number = e_number

        if e_number == 1:
            self.group = 1
            self.period = 1
        elif e_number == 2:
            self.group = 18
            self.period = 1
        elif 2 < e_number <= 4:
            self.group = e_number - 2
            self.period = 2
        elif 4 < e_number <= 10:
            self.group = e_number + 8
            self.period = 2
        elif 10 < e_number <= 12:
            self.group = e_number - 10
            self.period = 3
        elif 12 < e_number <= 18:
            self.group = e_number
            self.period = 3
        elif 18 < e_number <= 36:
            self.group = e_number - 18
            self.period = 4
        elif 36 < e_number <= 54:
            self.group = e_number - 36
            self.period = 5
        elif 54 < e_number <= 56:
            self.group = e_number - 54
            self.period = 6
        elif 56 < e_number <= 70:
            self.group = -1
            self.period = 6
        elif 70 < e_number <= 86:
            self.group = e_number - 70
            self.period = 6
        elif 86 < e_number <= 88:
            self.group = e_number - 86
            self.period = 7
        elif 88 < e_number <= 102:
            self.group = -2
            self.period = 7
        elif 102 < e_number <= 118:
            self.group = e_number - 102
            self.period = 7

        if 1 < self.group <= 10 or self.group < 0:
            self.valence_e = 2
        elif 10 < self.group <= 18:
            self.valence_e = self.group % 10
        elif self.group == 1:
            self.valence_e = 1

        if self.period >= 3:
            self.extend = True
        else:
            self.extend = False
        self.case_first = []
        self.case = [[] for i in range(8)]
        if self.period == 1:
            for i in range(3):
                for j in range(2):
                    for k in range(1):
                        for m in range(1):
                            if 2*i + 4*j + 6*k + 2*m == 2:
                                    formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                    self.case_first.append((i,j,k,m,formalcharge))
        else:
            for i in range(5):
                for j in range(3):
                    for k in range(2):
                        for m in range(4):
                            if 2*i + 4*j + 6*k + 2*m == 8:
                                    formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                    self.case_first.append((i,j,k,m,formalcharge))
        if self.extend and self.valence_e >= 5:
            for i in range(6):
                for j in range(3):
                    for k in range(2):
                        for m in range(5):
                            if 2*i + 4*j + 6*k + 2*m == 10:
                                formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                self.case_first.append((i,j,k,m,formalcharge))
        if self.extend and self.valence_e >= 6:
            for i in range(7):
                for j in range(4):
                    for k in range(3):
                        for m in range(6):
                            if 2*i + 4*j + 6*k + 2*m == 12:
                                formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                self.case_first.append((i,j,k,m,formalcharge))
        if self.extend and self.valence_e >= 7:
            for i in range(8):
                for j in range(4):
                    for k in range(3):
                        for m in range(7):
                            if 2*i + 4*j + 6*k + 2*m == 14:
                                formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                self.case_first.append((i,j,k,m,formalcharge))
        if self.extend and self.valence_e >= 8:
            for i in range(9):
                for j in range(5):
                    for k in range(3):
                        for m in range(8):
                            if 2*i + 4*j + 6*k + 2*m == 16:
                                formalcharge = self.valence_e - (i + 2*j + 3*k + 2*m)
                                self.case_first.append((i,j,k,m,formalcharge))
        for i in self.case_first:
            self.case[abs(i[4])].append(i)
'''
H =Element(118,2)
print(H.group)
print(H.period)
print(H.valence_e)
print(H.case)
'''
for i in range(1, 119):
    globals()['{}'.format(element[i])]= Element(i,electronegativity[i])
a = 1
b = 2
Matrix = [[0 for i in range(5)] for j in range(5)]
Matrix1 = [[0 for i in range(5)] for j in range(5)]
figure = [[a,a,a,b,0],[a,a,0,0,0],[a,b,0,0,0],[a,b,0,0,0],[a,b,0,0,0]]
for i in Matrix:
    for j in i:
        if j > i:
            Matrix1[i][j] = 
        elif i == j :
            Matrix1[i][j] = 0
        else:
            Matrix1[i][j] = Matrix1[j][i]

class Atom:
    def __init__(self, single, double, triple, lonepair, formalcharge, electronegativity):
        self.single = single
        self.double = double
        self.triple = triple
        self.lonepair = lonepair
        self.formalcharge = formalcharge
        self.electronegativity = electronegativity
        self.branch = single + double + triple
        for i in range(self.branch):
            globals()['self.branch{}'.format(i+1)] = True

def interpretmolecule():
    subject = molecule.get()
    subjectlist_first = []
    subjectlist = []
    try:
        for i in subject:
            if 48 <= ord(i) <= 57 and 48 <= ord(subjectlist_first[-1]) <= 57:
                subjectlist_first[-1] += i
            elif 97 <= ord(i) <= 122:
                subjectlist_first[-1] += i
            else:
                subjectlist_first.append(i)
        for i in range(len(subjectlist_first)):
            try:
                subjectlist_first[i] = int(subjectlist_first[i])
            except ValueError:
                for j in range(1, 119):
                    if globals()['{}'.format(element[j])].e_number == i+1:
                        subjectlist.append(globals()['{}'.format(element[j])])
                        print(subjectlist)
                        break
            else:
                for j in range(subjectlist_first[i]-1):
                    subjectlist.append(subjectlist[-1])
    except Exception as e:
        messagebox.showerror(title = 'Interpret error', message= 'This is not a molecule fomula. Please correct it.')
        return 'Try it again'
    
mainwindow = Tk()
mainwindow.title("Drawing Lewis Structure")
mainwindow.geometry("1000x1000")
mainwindow.iconphoto(True, PhotoImage(file = "C:\\Users\\82109\\Desktop\\Lewis\\Lewisicon.png"))
mainwindow.config(background='whitesmoke')

Empty1 = Label(mainwindow,
               padx = 73)
              
title = Label(mainwindow, text = "Drawing Lewis Structure",
              font = ('Arial', 40, 'bold'),
              fg = 'white',
              bg = 'lightgray',
              #relief = RAISED,
              bd = 10,
              padx = 10,
              pady = 5)

Empty2 = Label(mainwindow,
               pady = 10)

moleculebutton = Button(mainwindow,
                 font = ('Arial', 20, 'bold'),
                 text = 'submit',
                 command = interpretmolecule,
                 fg = 'white',
                 bg = 'lightgray',
                 relief = FLAT,
                 activebackground= 'lightgray',
                 activeforeground= 'white',
                 bd = 10,
                 pady = 5)

molecule = Entry(mainwindow,
                 font = ('Arial', 40, 'bold'),
                 fg = 'white',
                 bg = 'lightgray',
                 #relief = RAISED,
                 bd = 10,
                 width = 22)
molecule.insert(0,'write molecule fomula.')

Empty3 = Label(mainwindow,
               pady = 10)

drawer = Canvas(mainwindow,
                height = 650,
                width = 650,
                bg = 'white',
                relief = SOLID,
                borderwidth=2)
#drawer.create_line([100,1,100,70], fill="black", width = 5)
#drawer.create_oval([50,50,60,60], fill="black")
#drawer.create_oval([50,75,60,85], fill="black")
#drawer.create_oval([50,50,60,60], fill="black")
#drawer.create_text(100,100, text = 'C', fill = 'black', font = ('Arial', 40, 'bold'))
Empty1.grid(column = 0, row = 0)
title.grid(column = 2, row = 0)
Empty2.grid(column = 0, row = 1)
moleculebutton.grid(column = 3, row = 2)
molecule.grid(column = 2, row = 2)
Empty3.grid(column = 0, row = 3)
drawer.grid(column = 2, row = 4)
mainwindow.mainloop()
