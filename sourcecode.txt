from tkinter import *
from functools import *
from tkinter import messagebox
import random
import sqlite3

root=Tk()
root.geometry('1600x750')
#root.configure(bg="pink")

class score:
    right=0
    wrong=0
    def __init__(self):
        self.right=0
        self.wrong=0
        
    def right_ans(self):
        self.right=self.right+1
        print('new right score ',self.right)
    def wrong_ans(self):
        self.wrong=self.wrong+1    
    def total_right(self):
        return self.right
    def total_wrong(self):
        return self.wrong

s=score()        # creating score class object


def disp_result(sc):
    win=Tk()
    win.geometry('500x300')
    
    l1=Label(win,text='Right answers: '+str(sc.total_right()),font=('times new roman',30,'bold'))
    l1.place(x=20,y=20)
    l2=Label(win,text='Wrong answers: '+str(sc.total_wrong()),font=('times new roman',30,'bold'))
    l2.place(x=20,y=120)
    print('Right answers: ',sc.right)
    print('Wrong answers: ',sc.wrong)
    win.mainloop()

def image(string):
    frame_option.destroy()
    s1=score()

    if(string=='Easy Image Question'):
        def easy_image():
            def clr():
                butt_frame.destroy()
                image_frame.destroy()
                ani_frame.destroy()
                easy_image()
            
            def check(inp):
                if name==inp:
                    messagebox.showinfo("successfull","won the game")
                    s1.right_ans()
                    clr()
                else:
                    s1.wrong_ans()
                    ans=messagebox.askquestion("failed","sorry wanna try again")
                    if(ans!='yes'):
                        clr()
                    
            image_frame=Frame(root,width=1600,height=750,bg='red')
            image_frame.place(x=0,y=0)
            
            g=["dog","elephant","horse","lion","monkey","rabbit"]    
            name=random.choice(g)
            
            ani_frame=Frame(root, bg="pink")
            ani_frame.pack(side=TOP, fill=X)
            image_lable=Label(ani_frame,width=700,height=350)
            img_loc=name+".png"
            image_lable.img=PhotoImage(file=img_loc)
            image_lable["image"]=image_lable.img
            image_lable.pack()
            
            butt_frame=Frame(root,bg='yellow')
            butt_frame.pack()
            p="dog"
            but1=Button(butt_frame,text=p,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,p))
            but1.pack(side=LEFT,padx=10)
            q="elephant"
            but2=Button(butt_frame,text=q,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,q))
            but2.pack(side=LEFT,padx=10)
            r="horse"
            but3=Button(butt_frame,text=r,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,r))
            but3.pack(side=LEFT,padx=10)
            s="lion"
            but6=Button(butt_frame,text=s,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,s))
            but6.pack(side=LEFT,padx=10)
            t="monkey"
            but4=Button(butt_frame,text=t,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,t))
            but4.pack(side=LEFT,padx=10)
            u="rabbit"
            but5=Button(butt_frame,text=u,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,u))
            but5.pack(side=LEFT,padx=10)    
            
            result_show=Button(root,text='Result',width=6,font=('times new roman',20,'bold'),command=lambda:disp_result(s1))
            result_show.place(x=1100,y=550)
            quit_button=Button(root,text='Quit',width=4,font=('times new roman',20,'bold'),command=root.destroy)
            quit_button.place(x=1250,y=550)
        easy_image()
    elif(string=='Medium Image Question'):
        def med_image():
            def clr():
                butt_frame.destroy()
                image_frame.destroy()
                ani_frame.destroy()
                med_image()
            
            def check(inp):
                if name==inp:
                    messagebox.showinfo("successfull","won the game")
                    s1.right_ans()
                    clr()
                else:
                    s1.wrong_ans()
                    ans=messagebox.askquestion("failed","sorry wanna try again")
                    if(ans!='yes'):
                        clr()
            
            image_frame=Frame(root,width=1920,height=1080,bg='red')
            image_frame.place(x=0,y=0)
            
            g=["truck","bus","ship","tractor","car","aeroplane"]    
            name=random.choice(g)
            
            ani_frame=Frame(root, bg="pink")
            ani_frame.pack(side=TOP, fill=X)
            image_lable=Label(ani_frame,width=700,height=350)
            img_loc=name+".png"
            image_lable.img=PhotoImage(file=img_loc)
            image_lable["image"]=image_lable.img
            image_lable.pack()
            
            butt_frame=Frame(root,bg='yellow')
            butt_frame.pack()
            p="truck"
            but1=Button(butt_frame,text=p,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,p))
            but1.pack(side=LEFT,padx=10)
            q="bus"
            but2=Button(butt_frame,text=q,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,q))
            but2.pack(side=LEFT,padx=10)
            r="ship"
            but3=Button(butt_frame,text=r,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,r))
            but3.pack(side=LEFT,padx=10)
            s="tractor"
            but6=Button(butt_frame,text=s,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,s))
            but6.pack(side=LEFT,padx=10)
            t="car"
            but4=Button(butt_frame,text=t,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,t))
            but4.pack(side=LEFT,padx=10)
            u="aeroplane"
            but5=Button(butt_frame,text=u,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,u))
            but5.pack(side=LEFT,padx=10)    
            
            result_show=Button(root,text='Result',width=6,font=('times new roman',20,'bold'),command=lambda:disp_result(s1))
            result_show.place(x=1100,y=550)
            quit_button=Button(root,text='Quit',width=4,font=('times new roman',20,'bold'),command=root.destroy)
            quit_button.place(x=1250,y=550)
        med_image()
    elif(string=='Hard Image Question'):
        def hard_image():
            def clr():
                butt_frame.destroy()
                image_frame.destroy()
                ani_frame.destroy()
                hard_image()
            
            def check(inp):
                if name==inp:
                    messagebox.showinfo("Message","Correct Answer")
                    s1.right_ans()
                    clr()
                else:
                    s1.wrong_ans()
                    ans=messagebox.askquestion("Message","Incorrect Answer")
                    if(ans!='yes'):
                        clr()
            
            image_frame=Frame(root,width=1920,height=1080,bg='red')
            image_frame.place(x=0,y=0)
            
            g=["guitar","violin","piano","flute","clarinet","trumpet"]    
            name=random.choice(g)
            
            ani_frame=Frame(root, bg="pink")
            ani_frame.pack(side=TOP, fill=X)
            image_lable=Label(ani_frame,width=700,height=350)
            img_loc=name+".png"
            image_lable.img=PhotoImage(file=img_loc)
            image_lable["image"]=image_lable.img
            image_lable.pack()
            
            butt_frame=Frame(root,bg='yellow')
            butt_frame.pack()
            p="guitar"
            but1=Button(butt_frame,text=p,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,p))
            but1.pack(side=LEFT,padx=10)
            q="violin"
            but2=Button(butt_frame,text=q,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,q))
            but2.pack(side=LEFT,padx=10)
            r="piano"
            but3=Button(butt_frame,text=r,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,r))
            but3.pack(side=LEFT,padx=10)
            s="flute"
            but6=Button(butt_frame,text=s,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,s))
            but6.pack(side=LEFT,padx=10)
            t="clarinet"
            but4=Button(butt_frame,text=t,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,t))
            but4.pack(side=LEFT,padx=10)
            u="trumpet"
            but5=Button(butt_frame,text=u,font="calibri 20 bold italic",bg="orange",fg="black",bd=5,width=10,command=partial(check,u))
            but5.pack(side=LEFT,padx=10)    
            
            result_show=Button(root,text='Result',width=6,font=('times new roman',20,'bold'),command=lambda:disp_result(s1))
            result_show.place(x=1100,y=550)
            quit_button=Button(root,text='Quit',width=4,font=('times new roman',20,'bold'),command=root.destroy)
            quit_button.place(x=1250,y=550)
        hard_image()
    
def number(string):
    frame_option.destroy()
    #print(button['text'])
    def check(valt):
        a=valt
        b=str(val[pos])
        if(a==b):
            messagebox.showinfo("Message","Correct Answer")
            number_frame.destroy()
            button_frame.destroy()
            s.right_ans()
            number(string)
        else:
            s.wrong_ans()
            ans=messagebox.askquestion("Message","Incorrect Answer")
            if(ans!='yes'):
                number_frame.destroy()
                button_frame.destroy()
                number(string)

    if(string=='Easy Number Question'):############################################################ Number level
        print('Coming to found==1')
        li=["five","six","seven","one","two","three","four","eight","nine"]
        val=[5,6,7,1,2,3,4,8,9]
    elif(string=='Medium Number Question'):
        print('Coming to found==2')
        li=["Fifty five","Seventy six","seventy one","twenty one","thirty two","fourty three","fifty four","sixty eight","twenty nine"]
        val=[55,76,71,21,32,43,54,68,29]
    elif(string=='Hard Number Question'):    
        li=["Nine thousand nine Hundred Fifty five","Seven Thousand Seven Hundred Seventy six","Eighty Thousand one Hundred seventy one","Two Hundred twenty one","Five Hundred thirty two","Four Hundred fourty three","Seven Hundred fifty four","Two Hundred sixty eight","One Hundred twenty nine"]
        val=[9955,7776,8171,221,532,443,754,268,129]######################################################

    copy_of_val=val[:]     # copying the values
    m=random.choice(li)
    pos=li.index(m)       ###############################index of number name##############################3
    print('Print: ',copy_of_val)
        
    number_frame=Frame(root,bg='orange',height=750,width=1600)
    number_frame.pack()
    
    la=Label(number_frame,text=m,bg="black",fg="white",font=("times new roman",80,"bold"))
    la.pack(fill=X)
        
    finlist=[]
    for i in range(7):
        b=random.choice(copy_of_val)
        finlist.append(b)
        copy_of_val.remove(b)
            
    if (val[pos] in finlist):
        finlist.remove(val[pos])
    finlist.append(val[pos])

    bu=[]
    button_frame=Frame(root,bg='red',height=200,width=800)
    button_frame.place(x=220,y=300)
    print(finlist)
    for i in range(len(finlist)):
        for j in range(len(finlist)):
            p1=random.choice(finlist)
            finlist.remove(p1)
            bu.append(Button(button_frame,text=str(p1),width=3,font=('times new roman',30,'bold'),bd=5,relief=RAISED,bg='white',command=partial(check,str(p1))))
            bu[-1].pack(side=LEFT,padx=20,pady=20)
    result_show=Button(root,text='Result',width=6,font=('times new roman',20,'bold'),command=lambda:disp_result(s))
    result_show.place(x=1100,y=550)
    quit_button=Button(root,text='Quit',width=4,font=('times new roman',20,'bold'),command=root.destroy)
    quit_button.place(x=1250,y=550)


def option():
    global frame_option
        
    frame_option=Frame(root,height=750,width=1600)
    frame_option.pack()

    #top_frame.destroy()
    #login_frame.destroy()
    
    select_label=Label(frame_option,text='Please select difficulty level of Questions',font=("times new roman",20,"bold"))
    select_label.place(x=100,y=40)
    
    enq='Easy Number Question'
    easy_num_button=Button(frame_option,text=enq,font=("times new roman",20,"bold"),command=lambda:number('Easy Number Question'))
    easy_num_button.place(x=120,y=200)
    eiq='Easy Image Question'
    easy_img_button=Button(frame_option,text=eiq,font=("times new roman",20,"bold"),command=lambda:image('Easy Image Question'))
    easy_img_button.place(x=120,y=300)
    
    mnq='Medium Number Question'
    med_num_button=Button(frame_option,text=mnq,font=("times new roman",20,"bold"),command=lambda:number('Medium Number Question'))
    med_num_button.place(x=520,y=200)
    miq='Medium Image Question'
    med_img_button=Button(frame_option,text=miq,font=("times new roman",20,"bold"),command=lambda:image('Medium Image Question'))
    med_img_button.place(x=520,y=300)

    hnq='Hard Number Question'
    hard_num_button=Button(frame_option,text=hnq,font=("times new roman",20,"bold"),command=lambda:number('Hard Number Question'))
    hard_num_button.place(x=920,y=200)
    hiq='Hard Image Question'
    hard_img_button=Button(frame_option,text=hiq,font=("times new roman",20,"bold"),command=lambda:image('Hard Image Question'))
    hard_img_button.place(x=920,y=300)

def game():###############################################################################################################
    top_frame.destroy()
    e_name=username_entry.get()#username enter
    e_pass=password_entry.get()#password enter
    found=False
    con=sqlite3.connect('game.db')
    c=con.execute("select * from sign_up")
    for x in c:
        if(e_name==x[0] and e_pass==x[1]):#checks from sign up
            found=True
            break
        else:
            found=False
    con.commit()

    if (found==True and (e_name!="" and e_pass!='')):
        login_frame.destroy()  
        option()
    else:
        messagebox.showinfo("Message", "Username or Password is wrong")##################################################

top_frame=Frame(root,bg='yellow',height=1080,width=1920)
top_frame.pack()
top_label=Label(top_frame, text="Welcome to Kids Learning Game",bg="black",fg="white",font=("times new roman",58,"bold italic"))
top_label.place(x=200,y=50)

mid_label=Label(top_frame,text="Number and Image Guessing Game",bg="black",fg="white",font=("times new roman",34,'bold'))
mid_label.place(x=350,y=180)

login_frame=Frame(root,bg='black',height=400,width=500)
login_frame.place(x=420,y=250)

username_label=Label(login_frame,text='Username',bg='white',font=('times new roman',20,'bold'))
username_label.place(x=40,y=80)
username_entry=Entry(login_frame,font=('times new roman',20,'bold'))
username_entry.place(x=200,y=80)

password_label=Label(login_frame,text='Password',bg='white',font=('times new roman',20,'bold'))
password_label.place(x=40,y=180)
password_entry=Entry(login_frame,font=('times new roman',20,'bold'))
password_entry.place(x=200,y=180)

def sign_up():
    win=Tk()
    win.title('Sign up')
    win.geometry('750x450')
    win.configure(bg='Orange')
    
    def save_data():
        print('Data saved')
        found=False
        password=pass_entry.get()
        mobile=int(name_entry.get())

        
        def check():
            if(mobile>6000000000 and mobile<10000000000):
                found=True
            else:
                found=False
                ans=messagebox.askquestion('Warning','Not valid number...Want to try again')
                if(ans=='yes'):
                    win.destroy()
                    sign_up()
        check()
        
        if((mobile=='' or password=='') and found==False):
            message=messagebox.showinfo('Warning: ','Enter the correct data')
        else:
            con=sqlite3.connect('game.db')
            #con.execute("create table sign_up(username varchar(50),password varchar(50));")
            con.execute("insert into sign_up(username,password)values(?,?)",(mobile,password))
            con.commit()
            win.destroy()
            message=messagebox.showinfo('Congrats: ','Account Created Successfully')
            con.commit()
    
    name_label=Label(win,text='Enter Mobile No:',fg='white',font=('times new roman',15,'bold'),bg='black',padx=10,pady=5)
    name_label.place(x=100,y=90)
    name_entry=Entry(win,font=('times new roman',20,'bold'))
    name_entry.place(x=350,y=90)
    
    pass_label=Label(win,text=' Password ',fg='white',font=('times new roman',15,'bold'),bg='black',padx=10,pady=5)
    pass_label.place(x=100,y=200)
    pass_entry=Entry(win,font=('times new roman',20,'bold'))
    pass_entry.place(x=350,y=200)
    sign_button=Button(win,text=' Sign up ',fg='white',font=('times new roman',15,'bold'),bg='black',command=save_data)
    sign_button.place(x=300,y=330)
           
    win.mainloop()

signup_button=Button(login_frame,text='Sign up',font=('times new roman',15,'bold'),bg='Orange',command=sign_up)
signup_button.place(x=120,y=300)

login_button=Button(login_frame,text='LogIn',font=('times new roman',15,'bold'),bg='Green',command=game)
login_button.place(x=270,y=300)


root.mainloop()
