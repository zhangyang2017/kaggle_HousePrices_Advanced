# dataframes
1. train_set (to train models)
2. test_set  (to test algorithms only)
3. housing (train set without target value)
4. housing_labels (target value of the train set)

# EDA
- 45 catagorical attributes
- 34 numerical attributes
- drop
1. Utilities
2. Heating
3. RoofMatl
4. SaleCondition
5. Electrical
6. SaleType
7. PoolQC
8. MiscFeature
9. Street
10. Functional
11. MSSubClass
12. LandSlope
13. HouseStyle
14. YearBuilt
15. GarageYrBlt
16. MoSold
17. MiscVal
18. FullBath
19. HalfBath
20. BsmtFullBath
21. BsmtHalfBath
22. LowQualFinSF
23. PoolArea
24. YrSold
25. YearRemodAdd
26. 1stFlrSF
27. 2ndFlrSF
28. BsmtFinSF1
29. BsmtFinSF2
30. BsmtUnfSF
31. OpenPorchSF
32. EnclosedPorch
33. ScreenPorch
34. 3SsnPorch
35. GarageCars
36. KitchenAbvGr
37. BedroomAbvGr
further dropped:
38. OverallCond
39. ExterCond
40. LandContour
41. Condition2
42. Exterior1st
43. Exterior2nd
44. BsmtFinType1
45. BsmtFinType2
46. GarageFinish
47. MSZoning

- xxx original attributes
1. LotFrontage
2. LotArea
3. WoodDeckSF
4. MasVnrArea
5. GrLivArea
6. TotalBsmtSF
7. GarageArea
8. TotRmsAbvGrd

- xxx converted
1. LotConfig
	- CulDSac	0 least traffic
	- Inside	1
	- Corner	2
	- FR2	    2
	- FR3	    3  most traffic
2. BldgType
	- 1Fam	  0 no shared wall
	- Duplx	  1
	- TwnhsE  1
	- 2FmCon  2
	- Twnhs   2 most shared wall
3. RoofStyle: Gable: 1, others: 0
4. MasVnrType: None: 0, others: 1
5. Fence: Yes 1, No 0
6. CentralAir: Y 1, N 0
7. Alley: Y 1, N 0
8. LandContour: flat 1, others 0
9. Foundation: PConc: 1, others 0
10. Fireplaces: 0: 0, others: 1
11. LotShape: Reg: 1, others: 0
12. PavedDrive: Y: 1, others: 0
13. GarageType
14. BsmtExposure
15. Neighborhood: N-0, W-1, S-2, E-3 of campus


- xxx new attributes
1. HouseAge: YrSold - YearBuilt	
2. GarageAge: YrSold - GarageYrBlt
3. RecentRemodel: YrSold - YearRemodAdd
4. TotalPorch = OpenPorchSF + EnclosedPorch + ScreenPorch + 3SsnPorch
5. TotalBathAbGr: FullBath + HalfBath/2
6. TotalFinSF: BsmtFinSF1 + BsmtFinSF2 + 1stFlrSF + 2ndFlrSF
7. BsmtBath: 0: 0, others:1
8-12. GarageCond, GarageQual, FireplaceQu, BsmtQual, BsmtCond
	Po, None 0
	Fa 1
	TA 2
	Gd 3
	Ex 4
13-16. HeatingQC, ExterCond, ExterQual, KitchenQual
	Po 0
	Fa 1
	TA 2
	Gd 3
	Ex 4
17-18. OverallQual, OverallCond
19. Condition1: 0, railroad; 1, high traffic; 2, low traffic



from sklearn.preprocessing import LabelEncoder
gle = LabelEncoder()
genre_labels = gle.fit_transform(vg_df['Genre'])
genre_mappings = {index: label for index, label in 
                  enumerate(gle.classes_)}
genre_mappings
