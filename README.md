from tkinter import*
import math,random,os
from  tkinter import messagebox
class Bill_App:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1350x700+0+0")
        self.root.title("billg software")
        bg_color="#074463"
        title=Label(self.root,text="billing software",bd=10,relief=GROOVE,bg=bg_color,fg="white",font=("times new roman",30,"bold"),pady=2).pack(fill=X)
        #VARIABLE+++=============================
                                   #Cosmetics
        self.Soap=IntVar()
        self.Facecream=IntVar()
        self.Facewash=IntVar()
        self.Hairspray=IntVar()
        self.Hairgell=IntVar()
        self.Bodyloshan=IntVar()

                                   #Grocery
        self.Rice=IntVar()
        self.Tea=IntVar()
        self.Oil=IntVar()
        self.Milk=IntVar()
        self.Wheat=IntVar()
        self.Sugar=IntVar()
                                   #cold_drinks
        self.Maza=IntVar()
        self.Frooti=IntVar()
        self.Sprite=IntVar()
        self.cola=IntVar()
        self.Limca=IntVar()
        self.Thumbs_up=IntVar()
                                   #Total_product
        self.Cosmetic_price=StringVar()
        self.Grocery_price=StringVar()
        self.cold_drinks_price=StringVar()

        self.Cosmetic_tax=StringVar()
        self.Grocery_tax=StringVar()
        self.cold_drinks_tax=StringVar()
                                   #Customer
        self.Customer_name=StringVar()
        self.Customer_no=StringVar()

        self.Customer_Bill=StringVar()
        x=random.randint(1000,9999)
        self.Customer_Bill.set(str(x))
        self.Search_bill=StringVar()



        #===================customer_Details_Frame=====
        F1=LabelFrame(self.root,text="Customer Details",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
        F1.place(x=0,y=80,relwidth=1)
        customer_label=Label(F1,text="Customer Name:",bg=bg_color,fg="white",font=("times new roman",15,"bold")).grid(row=0,column=0,padx=0,pady=0)
        customer_text=Entry(F1,width=15,textvariable=self.Customer_name,font="arial 15",bd=6,relief=SUNKEN).grid(row=0,column=1,pady=5,padx=10)
         #===
        customer_phone=Label(F1,text="Phone No:",bg=bg_color,fg="white",font=("times new roman",15,"bold")).grid(row=0,column=2,padx=20,pady=5)
        customer_phonetext=Entry(F1,width=15,textvariable=self.Customer_no,font="arial 15",bd=6,relief=SUNKEN).grid(row=0,column=3,padx=10,pady=5)
        customer_bill=Label(F1,text="Customer bill:",bg=bg_color,fg="white",font=("times new roman",15,"bold")).grid(row=0,column=4,padx=20,pady=5)
        customer_billtext=Entry(F1,width=15,textvariable=self.Search_bill,font="axial 15",bd=6,relief=SUNKEN).grid(row=0,column=5,padx=10,pady=5)
        #==
        bill_button=Button(F1,text="Search",command=self.find_bill,width=10,bd=6,font="arial 12 bold").grid(row=0,column=6,padx=10,pady=10)
        #====
        F2=LabelFrame(self.root,bd=10,text="Cosmetics",bg=bg_color,fg="gold",font=("times new roman",15,"bold"))
        F2.place(x=5,y=170,width=325,height=380)

        soap_label=Label(F2,text=" Bath soap:",font=("times new roman",16,"bold"),bg=bg_color,fg="lightgreen").grid(row=0,column=0,padx=10,pady=10)
        soap_text=Entry(F2,width=10,textvariable=self.Soap,font=("times new roman",16,"bold"),bd=5,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=10)

        facecream_label= Label(F2, text="Face cream:", font=("times new roman", 16, "bold"), bg=bg_color,fg="lightgreen").grid(row=1, column=0, padx=10, pady=10)
        facecream_text = Entry(F2, width=10,textvariable=self.Facecream, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=1, column=1,padx=10,pady=10)

        Facewash_label = Label(F2, text="Face wash:", font=("times new roman", 16, "bold"), bg=bg_color,fg="lightgreen").grid(row=2, column=0, padx=10, pady=10)
        facewash_text = Entry(F2, width=10,textvariable=self.Facewash ,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=2, column=1,padx=10,pady=10)

        Hairspray_label = Label(F2, text="Hair spray:", font=("times new roman", 16, "bold"), bg=bg_color,fg="lightgreen").grid(row=3, column=0, padx=10, pady=10)
        hairspray_text = Entry(F2, width=10,textvariable=self.Hairspray,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=3, column=1,padx=10,pady=10)

        Hairgell_label = Label(F2, text="Hair gell:", font=("times new roman", 16, "bold"), bg=bg_color,fg="lightgreen").grid(row=4, column=0, padx=10, pady=10)
        hairgell_text = Entry(F2, width=10,textvariable=self.Hairgell ,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=4, column=1,padx=10,pady=10)

        Bodyloshan_label = Label(F2, text="Body loshan:", font=("times new roman", 16, "bold"), bg=bg_color,fg="lightgreen").grid(row=5, column=0, padx=10, pady=10)
        bodyloshan_text = Entry(F2, width=10,textvariable=self.Bodyloshan ,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=5, column=1,padx=10,pady=10)
        #===========Grocery frame=========
        F3=LabelFrame(self.root,bd=10,relief=GROOVE,text="Grocery",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
        F3.place(x=340,y=170,width=325,height=380)
        g1_label=Label(F3,text="Rice:",font=("times new roman",16,"bold"),bg=bg_color,fg="lightgreen").grid(row=0,column=0,padx=10,pady=10)
        g1_text = Entry(F3, width=10,textvariable=self.Rice ,font=("times new roman",16,"bold"), bd=5, relief=SUNKEN).grid(row=0, column=1,padx=10,pady=10)
        g2_label = Label(F3, text="Tea:", font=("times new roman", 16, "bold"), bg=bg_color, fg="lightgreen").grid(row=1,column=0, padx=10, pady=10)
        g2_text = Entry(F3, width=10,textvariable=self.Tea ,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=1, column=1,padx=10, pady=10)
        g3_label = Label(F3, text="Oil:", font=("times new roman", 16, "bold"), bg=bg_color, fg="lightgreen").grid(row=2,column=0, padx=10, pady=10)
        g3_text = Entry(F3, width=10,textvariable=self.Oil, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=2, column=1,padx=10, pady=10)
        g4_label = Label(F3, text="Milk:", font=("times new roman", 16, "bold"), bg=bg_color, fg="lightgreen").grid(row=3,column=0, padx=10, pady=10)
        g4_text = Entry(F3, width=10,textvariable=self.Milk, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=3, column=1,padx=10, pady=10)
        g5_label = Label(F3, text="wheat:", font=("times new roman", 16, "bold"), bg=bg_color, fg="lightgreen").grid(row=4, column=0, padx=10, pady=10)
        g5_text = Entry(F3, width=10, textvariable=self.Wheat,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=4, column=1,padx=10, pady=10)
        g6_label = Label(F3, text="Sugar:", font=("times new roman", 16, "bold"), bg=bg_color, fg="lightgreen").grid(row=5, column=0, padx=10, pady=10)
        g6_text = Entry(F3, width=10,textvariable=self.Sugar ,font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=5, column=1,padx=10, pady=10)
        #=========Cold Drinks Frame====
        F4=LabelFrame(self.root,bd=10,relief=GROOVE,text="Cold drinks",font=("times new roman ",15,"bold"),fg="gold",bg=bg_color)
        F4.place(x=670,y=170,width=325,height=380)
        w1_label = Label(F4,text="Maza:",font=("times new roman",16,"bold"),fg="lightgreen",bg=bg_color).grid(row=0,column=0,padx=10,pady=10)
        w1_text = Entry(F4,width=10,textvariable=self.Maza,font=("times new roman",16,"bold"),bd=5,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=10)
        w2_label = Label(F4, text="Frooti:", font=("times new roman", 16, "bold"), fg="lightgreen", bg=bg_color).grid(row=1, column=0, padx=10, pady=10)
        w2_text = Entry(F4, width=10,textvariable=self.Frooti, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=1, column=1,padx=10, pady=10)
        w3_label = Label(F4, text="Sprite:", font=("times new roman", 16, "bold"), fg="lightgreen", bg=bg_color).grid(row=2, column=0, padx=10, pady=10)
        w3_text = Entry(F4, width=10,textvariable=self.Sprite, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=2, column=1,padx=10, pady=10)
        w4_label = Label(F4, text="Cola:", font=("times new roman", 16, "bold"), fg="lightgreen", bg=bg_color).grid(row=3, column=0, padx=10, pady=10)
        w4_text = Entry(F4, width=10,textvariable=self.cola, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=3, column=1,padx=10, pady=10)
        w5_label = Label(F4, text="Limca:", font=("times new roman", 16, "bold"), fg="lightgreen", bg=bg_color).grid(row=4, column=0, padx=10, pady=10)
        w5_text = Entry(F4, width=10,textvariable=self.Limca, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=4, column=1,padx=10, pady=10)
        w6_label = Label(F4, text="Thumbs up:", font=("times new roman", 16, "bold"), fg="lightgreen", bg=bg_color).grid(row=5, column=0, padx=10, pady=10)
        w6_text = Entry(F4, width=10,textvariable=self.Thumbs_up, font=("times new roman", 16, "bold"), bd=5, relief=SUNKEN).grid(row=5, column=1,padx=10, pady=10)
        #Billarea
        F5=Frame(self.root,bd=10,relief=GROOVE)
        F5.place(x=1000,y=170,width=365,height=380)
        bill_title=Label(F5,text="Bill area",font="arial 15 bold",bd=7,relief=GROOVE).pack(fill=X)
        scrol_y = Scrollbar(F5,orient=VERTICAL)
        self.textarea= Text(F5,yscrollcommand=scrol_y.set)
        scrol_y.pack(side=RIGHT,fil=Y)
        scrol_y.config(command=self.textarea.yview)
        self.textarea.pack(fill=BOTH,expand=1)
        #Billframe
        F6=LabelFrame(self.root,bd=10,relief=GROOVE,text="Bill Menu",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
        F6.place(x=0,y=560,relwidth=1,height=140)
        m1_label=Label(F6,text="Total Cosmetics price:",fg="white",bg=bg_color,font=("times new roman",15,"bold")).grid(row=0,column=0,padx=20,pady=1,sticky="W")
        m1_text=Entry(F6,width=15,textvariable=self.Cosmetic_price,font="arial 10 bold",bd=7,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=1)
        m2_label = Label(F6, text="Total Grocery price:", fg="white", bg=bg_color,font=("times new roman", 15, "bold")).grid(row=1, column=0, padx=20, pady=1, sticky="W")
        m2_text = Entry(F6, width=15,textvariable=self.Grocery_price ,font="arial 10 bold", bd=7, relief=SUNKEN).grid(row=1, column=1, padx=10, pady=1)
        m3_label = Label(F6, text="Total Cold drinks price:", fg="white", bg=bg_color,font=("times new roman", 15, "bold")).grid(row=2, column=0, padx=20, pady=1, sticky="W")
        m3_text = Entry(F6, width=15,textvariable=self.cold_drinks_price, font="arial 10 bold", bd=7, relief=SUNKEN).grid(row=2, column=1, padx=10, pady=1)

        c1_label = Label(F6, text="Total Cosmetics tax", fg="white", bg=bg_color,font=("times new roman", 15, "bold")).grid(row=0, column=2, padx=20, pady=1, sticky="W")
        c1_text = Entry(F6, width=15, font="arial 10 bold", textvariable=self.Cosmetic_tax,bd=7, relief=SUNKEN).grid(row=0, column=3, padx=10, pady=1)
        c2_label = Label(F6, text="Total Grocery tax", fg="white", bg=bg_color,font=("times new roman", 15, "bold")).grid(row=1, column=2, padx=20, pady=1, sticky="W")
        c2_text = Entry(F6, width=15, font="arial 10 bold", textvariable=self.Grocery_tax,bd=7, relief=SUNKEN).grid(row=1, column=3, padx=10, pady=1)
        c3_label = Label(F6, text="Total Cold drinks tax", fg="white", bg=bg_color,font=("times new roman", 15, "bold")).grid(row=2, column=2, padx=20, pady=1, sticky="W")
        c3_text = Entry(F6, width=15, font="arial 10 bold", textvariable=self.cold_drinks_tax,bd=7, relief=SUNKEN).grid(row=2, column=3 , padx=10, pady=1)

        btn_f=Frame(F6,bd=7,relief=GROOVE)
        btn_f.place(x=750,width=590,height=105)

        total_btn=Button(btn_f,command=self.Total,text="Total",bg=bg_color,fg="white",bd=7,pady=15,width=9,font="arial 16 bold").grid(row=0,column=0,padx=5,pady=5)
        bill_btn = Button(btn_f, text="Bill",command=self.bill_area,bg=bg_color, fg="white", bd=7, pady=15, width=9,font="arial 16 bold").grid(row=0, column=1, padx=5, pady=5)
        clear_btn = Button(btn_f, text="Clear",command=self.clear_bill ,bg=bg_color, fg="white", bd=7, pady=15, width=9,font="arial 16 bold").grid(row=0, column=2, padx=5, pady=5)
        exit_btn = Button(btn_f, text="Exit",command=self.Exit_app ,bg=bg_color, fg="white", bd=7, pady=15, width=9,font="arial 16  bold").grid(row=0, column=3, padx=5, pady=5)
        self.welcome_bill()
    def Total(self):
        self.c_s_p=self.Soap.get()*40
        self.c_fc_p=self.Facecream.get()*120
        self.c_fw_p=self.Facewash.get()*50
        self.c_hs_p=self.Hairspray.get()*200
        self.c_hg_p=self.Hairgell.get()*160
        self.c_bl_c=self.Bodyloshan.get()*180

        self.Total_Cosmetic_price=float(
                                       self.c_s_p+
                                       self.c_fc_p+
                                       self.c_fw_p+
                                       self.c_hs_p+
                                       self.c_hg_p+
                                       self.c_bl_c
        )
        self.Cosmetic_price.set("Rs. "+str(self.Total_Cosmetic_price))
        self.C_tax=round((self.Total_Cosmetic_price*0.05),2)
        self.Cosmetic_tax.set("Rs. "+str(self.C_tax))
        ##########################
        self.c_r_p=self.Rice.get()*40
        self.c_o_p=self.Oil.get()*70
        self.c_m_p=self.Milk.get()*60
        self.c_t_p=self.Tea.get()*100
        self.c_w_p=self.Wheat.get()*30
        self.c_su_p=self.Sugar.get()*35
        self.Total_Grocery_price = float(
                                    self.c_r_p+
                                    self.c_o_p+
                                    self.c_m_p+
                                    self.c_t_p+
                                    self.c_w_p+
                                    self.c_su_p
        )
        self.Grocery_price.set("Rs. "+str(self.Total_Grocery_price))
        self.G_tax=round((self.Total_Grocery_price*0.5),2)
        self.Grocery_tax.set("Rs. "+str(self.G_tax))
        ############################
        self.c_ma_p=self.Maza.get()*50
        self.c_fr_p=self.Frooti.get()*40
        self.c_sp_p=self.Sprite.get()*45
        self.c_co_p=self.cola.get()*60
        self.c_li_p=self.Limca.get()*45
        self.c_th_p=self.Thumbs_up.get()*45
        self.Total_Cold_drinks_price = float(
                                        self.c_ma_p+
                                        self.c_fr_p+
                                        self.c_sp_p+
                                        self.c_co_p+
                                        self.c_li_p+
                                        self.c_th_p

        )
        self.cold_drinks_price.set("Rs. "+str(self.Total_Cold_drinks_price))
        self.Cd_tax=round((self.Total_Cold_drinks_price*0.05),2)
        self.cold_drinks_tax.set("Rs. "+str(self.Cd_tax))

        self.Total_bill=float(
            self.Total_Cosmetic_price+
            self.Total_Grocery_price+
            self.Total_Cold_drinks_price+
            self.C_tax+
            self.G_tax+
            self.Cd_tax
        )

    def welcome_bill(self):
        self.textarea.delete('1.0',END)
        self.textarea.insert(END,"\t=========Welcome to DYNA========")
        self.textarea.insert(END,f"\n Bill Number :{self.Customer_Bill.get()}")
        self.textarea.insert(END,f"\n Phone Number:{self.Customer_no.get()}")
        self.textarea.insert(END,f"\n Customer Name :{self.Customer_name.get()}")
        self.textarea.insert(END,f"\n =======================================")
        self.textarea.insert(END,f"\n Product\t\tQTY\t\tPrice")
        self.textarea.insert(END,f"\n =======================================")
    def bill_area(self):
        if self.Customer_name.get()=="" or self.Customer_no.get()=="":
            messagebox.showerror("error","Customer details are must")
        elif self.Cosmetic_price.get()=="Rs. 0.0" and self.Grocery_price.get()=="Rs. 0.0" and self.cold_drinks_price.get()=="Rs. 0.0":
            messagebox.showerror("error","No product purchased")
        else:

             self.welcome_bill()
        if self.Soap.get()!=0:
            self.textarea.insert(END,f"\n Soap\t\t {self.Soap.get()}\t\t {self.c_s_p}")
        if self.Facecream.get()!=0:
            self.textarea.insert(END, f"\n FaceCream\t\t {self.Facecream.get()}\t\t {self.c_fc_p}")
        if self.Facewash.get()!=0:
            self.textarea.insert(END,f"\n FaceWash\t\t {self.Facewash.get()}\t\t {self.c_fw_p}")
        if self.Hairspray.get()!=0:
            self.textarea.insert(END,f"\n HairSpray\t\t {self.Hairspray.get()}\t\t {self.c_hs_p}")
        if self.Hairgell.get()!=0:
            self.textarea.insert(END,f"\n HairGell\t\t {self.Hairgell.get()}\t\t {self.c_hg_p}")
        if self.Bodyloshan.get()!=0:
            self.textarea.insert(END,f"\n BodyLoshan\t\t {self.Bodyloshan.get()}\t\t {self.c_bl_c}")

        if self.Rice.get()!=0:
            self.textarea.insert(END,f"\n Rice\t\t {self.Rice.get()}\t\t {self.c_r_p}")
        if self.Tea.get()!=0:
            self.textarea.insert(END,f"\n Tea\t\t {self.Tea.get()}\t\t {self.c_t_p}")
        if self.Oil.get()!=0:
            self.textarea.insert(END,f"\n Oil\t\t {self.Oil.get()}\t\t {self.c_o_p}")
        if self.Milk.get()!=0:
            self.textarea.insert(END,f"\n Milk\t\t {self.Milk.get()}\t\t {self.c_m_p}")
        if self.Wheat.get()!=0:
            self.textarea.insert(END,f"\n Wheat\t\t {self.Wheat.get()}\t\t {self.c_w_p}")
        if self.Sugar.get()!=0:
            self.textarea.insert(END,f"\n Sugar\t\t {self.Sugar.get()}\t\t {self.c_su_p}")

        if self.Maza.get()!=0:
            self.textarea.insert(END,f"\n Maza\t\t {self.Maza.get()}\t\t {self.c_ma_p}")
        if self.Frooti.get()!=0:
            self.textarea.insert(END,f"\n Frooti\t\t {self.Frooti.get()}\t\t {self.c_fr_p}")
        if self.Sprite.get()!=0:
            self.textarea.insert(END,f"\n Sprite\t\t {self.Sprite.get()}\t\t {self.c_sp_p}")
        if self.cola.get()!=0:
            self.textarea.insert(END,f"\n Cola\t\t {self.cola.get()}\t\t {self.c_co_p}")
        if self.Limca.get()!=0:
            self.textarea.insert(END,f"\n Limca\t\t {self.Limca.get()}\t\t {self.c_li_p}")
        if self.Thumbs_up.get()!=0:
            self.textarea.insert(END,f"\n Thumbs up\t\t {self.Thumbs_up.get()}\t\t {self.c_th_p}")

        self.textarea.insert(END, f"\n ---------------------------------------")
        if self.Cosmetic_tax.get() != "Rs. 0.0":
            self.textarea.insert(END, f"\n Cosmetic tax\t\t\t{self.Cosmetic_tax.get()}")
        if self.Grocery_tax.get() != "Rs. 0.0":
            self.textarea.insert(END, f"\n Grocery tax\t\t\t{self.Grocery_tax.get()}")
        if self.cold_drinks_tax.get() != "Rs. 0.0":
            self.textarea.insert(END, f"\n Cold drinks\t\t\t{self.cold_drinks_tax.get()}")

        self.textarea.insert(END, f"\n Total Bill\t\t\tRs. {str(self.Total_bill)}")
        self.textarea.insert(END, f"\n ---------------------------------------")
        self.save_bill()
    def save_bill(self):
        op=messagebox.askyesno("save bill","do you want to save the bill?")
        if op>0:
            self.bill_data=self.textarea.get('1.0',END)
            f1=open("E:bills/"+str(self.Customer_Bill.get())+".txt","w")
            f1.write(self.bill_data)
            f1.close()
            messagebox.showinfo("saved ",f"bill no. :{self.Customer_Bill.get()} saved successfully")
        else:
            return
    def find_bill(self):
        present="no"
        for i in os.listdir("E:bills"):
            if i.split('.')[0]==self.Search_bill.get():
                f1=open(f"E:bills/{i}","r")
                self.textarea.delete('1.0',END)
                for d in f1:
                    self.textarea.insert(END,d)
                f1.close()
                present="yes"
        if present=="no":
            messagebox.showerror("Error","Invalid bill no.")
    def clear_bill(self):
        op = messagebox.askyesno("Clear", "Do you want to Clear data?")
        if op > 0:
            self.Soap.set(0)
            self.Facewash.set(0)
            self.Facewash.set(0)
            self.Hairspray.set(0)
            self.Hairgell.set(0)
            self.Bodyloshan.set(0)

            # Grocery
            self.Rice.set(0)
            self.Tea.set(0)
            self.Oil.set(0)
            self.Milk.set(0)
            self.Wheat.set(0)
            self.Sugar.set(0)
            # cold_drinks
            self.Maza.set(0)
            self.Frooti.set(0)
            self.Sprite.set(0)
            self.cola.set(0)
            self.Limca.set(0)
            self.Thumbs_up.set(0)
             # Total_product
            self.Cosmetic_price.set("")
            self.Grocery_price.set("")
            self.cold_drinks_price.set("")

            self.Cosmetic_tax.set("")
            self.Grocery_tax.set("")
            self.cold_drinks_tax.set("")
            # Customer
            self.Customer_name.set("")
            self.Customer_no.set("")

            self.Customer_Bill.set("")
            x = random.randint(1000, 9999)
            self.Customer_Bill.set(str(x))
            self.Search_bill.set("")
            self.welcome_bill()
    def Exit_app(self):
        op=messagebox.askyesno("Exit","Do you want to Exit?")
        if op>0:
            self.root.destroy()




root=Tk()
object = Bill_App(root)
root.mainloop()
